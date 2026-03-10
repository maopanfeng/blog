<!doctype html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width,initial-scale=1,shrink-to-fit=no">
    <title>Wiki - Ben Thinking</title>
    <style>
        body { margin: 0; padding: 0; background: #fff; color: #000; font-family: -apple-system, BlinkMacSystemFont, sans-serif; -webkit-font-smoothing: antialiased; display: flex; flex-direction: column; align-items: center; }
        header { position: fixed; top: 0; left: 0; right: 0; height: 80px; z-index: 9999; background: rgba(255,255,255,0.95); backdrop-filter: blur(20px); border-bottom: 1px solid rgba(0,0,0,0.05); display: flex; justify-content: center; }
        .nav-container { width: 100%; max-width: 720px; height: 100%; display: flex; align-items: center; justify-content: space-between; padding: 0 24px; box-sizing: border-box; }
        .logo-wrapper { display: flex; align-items: center; gap: 12px; text-decoration: none; color: inherit; }
        .site-logo { width: 32px; height: 32px; border-radius: 6px; }
        .site-title { font-weight: 800; font-size: 1.25rem; letter-spacing: -0.03em; }
        .nav-right { display: flex; align-items: center; gap: 20px; }
        .search-wrapper { display: flex; align-items: center; background: rgba(0,0,0,0.05); border-radius: 20px; padding: 6px 15px; }
        .search-box { background: transparent; border: none; font-size: 13px; width: 80px; outline: none; }
        
        main { width: 100%; max-width: 720px; margin: 120px auto 0; padding: 0 24px; position: relative; box-sizing: border-box; }
        
        #wiki-graph { width: 100%; height: 500px; background: #fafafa; border-radius: 12px; margin-bottom: 50px; border: 1px solid #f0f0f0; cursor: grab; }
        
        .post-list h2 { font-size: 1.2rem; font-weight: 800; margin-bottom: 30px; text-transform: uppercase; letter-spacing: 0.1em; opacity: 0.3; }
        .post-item { margin-bottom: 40px; display: block; text-decoration: none; color: inherit; }
        .post-title { font-size: 1.5rem; font-weight: 800; margin-bottom: 0.5rem; display: block; line-height: 1.3; }
        .post-title:hover { opacity: 0.6; }
        .post-date { opacity: 0.25; font-size: 0.8rem; font-family: monospace; }

        .sidebar-archive { position: absolute; left: calc(100% + 50px); top: 0; width: 100px; }
        .sidebar-archive h3 { font-size: 11px; opacity: 0.2; text-transform: uppercase; margin-bottom: 15px; }
        .sidebar-archive ul { list-style: none; padding: 0; margin: 0; font-size: 12px; line-height: 2.2; }
        .sidebar-archive span { cursor: pointer; opacity: 0.4; transition: 0.2s; display: block; }
        .sidebar-archive span:hover { opacity: 1; color: #000; }
        
        @media (max-width: 1150px) { .sidebar-archive { display: none; } }
    </style>
</head>
<body>
    <header>
        <div class="nav-container">
            <a href="/" class="logo-wrapper">
                <img src="/logo.png" alt="" class="site-logo">
                <span class="site-title">Ben Thinking</span>
            </a>
            <div class="nav-right">
                <div class="search-wrapper"><input type="text" class="search-box" placeholder="Search..." onkeyup="filterSearch(this.value)"></div>
                <a href="/cn/wiki" style="font-size:12px; opacity:0.4; text-decoration:none; color:inherit; font-weight:700;">中文</a>
            </div>
        </div>
    </header>

    <main>
        <aside class="sidebar-archive">
            <h3>Archive</h3>
            <ul>
                {{ range (seq 2026 -1 2024) }}
                <li><span onclick="filterYear('{{ . }}')" class="year-btn">{{ . }}</span></li>
                {{ end }}
            </ul>
        </aside>

        <div id="wiki-graph"></div>

        <div class="post-list" id="post-container">
            <h2>Knowledge Nodes</h2>
            {{ range where .Site.RegularPages "Section" "posts" }}
            <article class="post-item" data-year="{{ .Date.Format "2006" }}">
                <a href="{{ .Permalink }}" class="post-title">{{ .Title }}</a>
                <div class="post-date">{{ .Date.Format "2006-01-02" }}</div>
            </article>
            {{ end }}
        </div>
    </main>

    <script src="https://d3js.org/d3.v7.min.js"></script>
    <script>
        const nodes = [
            { id: "Complexity Economics", url: "/posts/complexity-economics/" },
            { id: "James Anderson", url: "/posts/lingotto/" },
            { id: "Lingotto", url: "/posts/lingotto/" },
            { id: "Scale", url: "/posts/scale/" },
            { id: "Nature of Technology", url: "/posts/nature-of-technology/" }
        ];

        const links = [
            { source: "James Anderson", target: "Lingotto" },
            { source: "Lingotto", target: "Complexity Economics" },
            { source: "Complexity Economics", target: "Nature of Technology" },
            { source: "Scale", target: "Complexity Economics" }
        ];

        const container = document.getElementById('wiki-graph');
        const width = container.clientWidth;
        const height = 500;

        const svg = d3.select("#wiki-graph").append("svg")
            .attr("width", width).attr("height", height);

        const sim = d3.forceSimulation(nodes)
            .force("link", d3.forceLink(links).id(d => d.id).distance(100))
            .force("charge", d3.forceManyBody().strength(-300))
            .force("center", d3.forceCenter(width / 2, height / 2));

        const link = svg.append("g").attr("stroke", "#eee").selectAll("line").data(links).join("line");

        const node = svg.append("g").selectAll("g").data(nodes).join("g")
            .style("cursor", "pointer")
            .on("click", (e, d) => { window.location.href = d.url; })
            .call(d3.drag().on("start", dragstarted).on("drag", dragged).on("end", dragended));

        node.append("circle").attr("r", 6).attr("fill", "#000");
        node.append("text").text(d => d.id).attr("x", 12).attr("y", 4).style("font-size", "11px").style("opacity", 0.5);

        sim.on("tick", () => {
            link.attr("x1", d => d.source.x).attr("y1", d => d.source.y).attr("x2", d => d.target.x).attr("y2", d => d.target.y);
            node.attr("transform", d => `translate(${d.x},${d.y})`);
        });

        function dragstarted(e, d) { if (!e.active) sim.alphaTarget(0.3).restart(); d.fx = d.x; d.fy = d.y; }
        function dragged(e, d) { d.fx = e.x; d.fy = e.y; }
        function dragended(e, d) { if (!e.active) sim.alphaTarget(0); d.fx = null; d.fy = null; }

        function filterSearch(query) {
            const posts = document.querySelectorAll('.post-item');
            posts.forEach(p => p.style.display = p.innerText.toLowerCase().includes(query.toLowerCase()) ? 'block' : 'none');
        }

        function filterYear(year) {
            const posts = document.querySelectorAll('.post-item');
            posts.forEach(p => p.style.display = (year === 'all' || p.getAttribute('data
