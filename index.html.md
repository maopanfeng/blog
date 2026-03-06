<!doctype html>
<html lang=zh-cn>
<head>
    <meta charset=utf-8>
    <meta name=viewport content="width=device-width,initial-scale=1,shrink-to-fit=no">
    <title>{{ .Site.Title }}</title>
    <link rel=stylesheet href=/main.css>
    <style>
        /* 1. 基础响应式布局 */
        body { margin:0; padding:0; min-height:100vh; display:flex; flex-direction:column; font-family:-apple-system,sans-serif; }
        
        /* 2. 导航栏与嵌入式搜索框 */
        header { position:fixed; top:0; left:0; right:0; height:80px; z-index:9999; border-bottom:1px solid rgba(0,0,0,6%); background-color:rgba(255,255,255,.9); backdrop-filter:blur(10px); }
        .nav-container { max-width:720px; height:100%; margin:0 auto; display:flex; align-items:center; justify-content:space-between; padding:0 24px; box-sizing:border-box; }
        .search-box { background: rgba(0,0,0,0.05); border: none; padding: 6px 12px; border-radius: 16px; font-size: 13px; width: 120px; transition: width 0.3s; }
        .search-box:focus { width: 180px; outline: none; background: rgba(0,0,0,0.08); }

        /* 3. Timeline 响应式设计：手机端自动隐藏 */
        .sidebar-archive { position:absolute; left:calc(100% + 40px); top:0; width:100px; }
        @media(max-width: 1150px) { .sidebar-archive { display: none !important; } }

        /* 4. 文章摘要与折叠样式 */
        .post-summary { opacity:.8; line-height:1.6; margin-top: 10px; }
        details summary { cursor: pointer; color: #666; font-size: 14px; margin-bottom: 8px; list-style: none; }
        details summary::-webkit-details-marker { display: none; }
        details[open] summary { margin-bottom: 12px; }
    </style>
</head>

<body class="dark:bg-black dark:text-white">
    <header class="dark:bg-black/90 dark:border-white/10">
        <div class="nav-container">
            <a href="/" style="display:flex;align-items:center;text-decoration:none;color:inherit;">
                <span style="font-size:1.15rem;font-weight:700;">Ben Thinking</span>
            </a>
            
            <nav style="display:flex;gap:15px;align-items:center">
                <input type="text" id="search-input" class="search-box" placeholder="搜索文章...">
                <a href="/wiki" style="text-decoration:none;color:inherit;font-size:14px;opacity:.6">Wiki</a>
                <a href="/about" style="text-decoration:none;color:inherit;font-size:14px;opacity:.6">关于</a>
            </nav>
        </div>