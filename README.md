# tencent-kf-demo
tencent-kf-demo
[tencent-kf.html](https://github.com/user-attachments/files/23503109/tencent-kf.html)
<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>腾讯客服 - 仿制示例</title>
<style>
:root {
  --primary-color: #0078d7;
  --secondary-color: #f5f7fa;
  --text-color: #333;
  --text-light: #666;
  --border-color: #e0e0e0;
  --max-width: 1200px;
}
* { margin:0; padding:0; box-sizing:border-box; }
body { font-family:'Helvetica Neue', Arial, sans-serif; color:var(--text-color); background:#fff; line-height:1.6; }
header { background:#fff; border-bottom:1px solid var(--border-color); position:sticky; top:0; z-index:100; transition:box-shadow 0.3s; }
.navbar { max-width:var(--max-width); margin:0 auto; display:flex; justify-content:space-between; align-items:center; padding:1rem 2rem; position:relative; }
.logo { font-size:1.5rem; font-weight:bold; color:var(--primary-color); text-decoration:none; }
.nav-menu ul { list-style:none; display:flex; gap:1.5rem; }
.nav-menu a { text-decoration:none; color:var(--text-color); transition:color 0.2s; }
.nav-menu a:hover { color:var(--primary-color); }
.hamburger { display:none; background:none; border:none; font-size:1.5rem; cursor:pointer; }
.hero { background:linear-gradient(135deg, #0078d7, #00a0e9); color:#fff; text-align:center; padding:4rem 2rem; position:relative; }
.hero h1 { font-size:2.5rem; margin-bottom:1rem; }
.hero p { font-size:1.2rem; margin-bottom:1rem; }
.cta-button { background:#fff; color:var(--primary-color); border:none; padding:0.8rem 1.5rem; border-radius:4px; font-weight:bold; cursor:pointer; transition:0.3s; margin-bottom:1rem; }
.cta-button:hover { background:var(--secondary-color); }
.search-bar { margin-top:1rem; display:flex; justify-content:center; gap:0.5rem; }
.search-bar input { padding:0.5rem; width:250px; border-radius:4px; border:none; outline:none; }
.search-bar button { padding:0.5rem 1rem; background:#fff; border:none; border-radius:4px; cursor:pointer; font-weight:bold; color:var(--primary-color); }
.search-bar button:hover { background:var(--secondary-color); }
.main-content { max-width:var(--max-width); margin:3rem auto; padding:0 1rem; }
.section { margin-bottom:3rem; }
.section h2 { color:var(--primary-color); border-left:4px solid var(--primary-color); padding-left:0.5rem; margin-bottom:1.5rem; }
.card-grid { display:grid; grid-template-columns:repeat(auto-fit,minmax(250px,1fr)); gap:1.5rem; }
.card { border:1px solid var(--border-color); border-radius:8px; background:#fff; padding:1.5rem; transition:transform 0.2s, box-shadow 0.2s; }
.card:hover { transform:translateY(-5px); box-shadow:0 4px 12px rgba(0,0,0,0.1); }
.card h3 { color:var(--text-color); margin-bottom:0.5rem; }
.card p { color:var(--text-light); font-size:0.95rem; }
.contact { text-align:center; background:var(--secondary-color); padding:2rem 1rem; }
.button { background:var(--primary-color); color:#fff; border:none; padding:0.8rem 1.5rem; border-radius:4px; font-size:1rem; cursor:pointer; transition:0.3s; margin:0.3rem; }
.button:hover { background:#005ea6; }
footer { background:#f2f4f8; color:var(--text-light); text-align:center; padding:1.5rem 1rem; font-size:0.9rem; border-top:1px solid var(--border-color); }
.footer-links { margin-bottom:0.5rem; }
.footer-links a { color:var(--text-light); text-decoration:none; margin:0 0.5rem; }
.footer-links a:hover { color:var(--primary-color); }

/* 聊天弹窗 */
#chat-box { display:none; position:fixed; bottom:20px; right:20px; width:320px; max-height:450px; background:#fff; border:1px solid var(--border-color); border-radius:8px; box-shadow:0 4px 12px rgba(0,0,0,0.2); flex-direction:column; }
#chat-header { background:var(--primary-color); color:#fff; padding:0.8rem; border-radius:8px 8px 0 0; font-weight:bold; }
#chat-messages { flex:1; padding:0.5rem; overflow-y:auto; background:#f9f9f9; font-size:0.9rem; }
#chat-input { display:flex; border-top:1px solid var(--border-color); }
#chat-input input { flex:1; border:none; padding:0.6rem; outline:none; }
#chat-input button { background:var(--primary-color); color:#fff; border:none; padding:0.6rem 1rem; cursor:pointer; }

/* 响应式 */
@media(max-width:768px){
  .nav-menu ul { flex-direction:column; gap:1rem; display:none; position:absolute; top:100%; left:0; width:100%; background:#fff; }
  .nav-menu.active ul { display:flex; }
  .hamburger { display:block; }
  .hero h1 { font-size:2rem; }
  .hero p { font-size:1rem; }
  .search-bar { flex-direction:column; }
}
</style>
</head>
<body>

<header>
  <div class="navbar">
    <a href="#" class="logo">腾讯客服</a>
    <button class="hamburger" aria-label="打开菜单">☰</button>
    <nav class="nav-menu">
      <ul>
        <li><a href="#help">帮助中心</a></li>
        <li><a href="#human">人工客服</a></li>
        <li><a href="#youth">未成年人保护</a></li>
        <li><a href="#report">举报中心</a></li>
        <li><a href="#login">登录</a></li>
      </ul>
    </nav>
  </div>
</header>

<section class="hero">
  <h1>欢迎访问腾讯客服中心</h1>
  <p>快速获取帮助与支持，解决您的产品使用问题</p>
  <button class="cta-button" id="open-chat">立即咨询</button>
  <div class="search-bar">
    <input type="search" id="faqSearch" placeholder="请输入关键词，如：充值失败">
    <button id="faqSearchBtn">搜索</button>
  </div>
</section>

<main class="main-content">
  <section class="section" id="help">
    <h2>热门问题</h2>
    <div class="card-grid">
      <div class="card"><h3>微信账号冻结</h3><p>通过微信安全中心自助解封或联系客服协助。</p></div>
      <div class="card"><h3>QQ无法登录</h3><p>尝试账号申诉或设备安全检测修复。</p></div>
      <div class="card"><h3>游戏充值未到账</h3><p>使用订单号查询并申请补发。</p></div>
    </div>
  </section>

  <section class="section contact" id="human">
    <h2>人工客服渠道</h2>
    <p>点击下面按钮即可联系在线客服或拨打热线</p>
    <button class="button" id="open-chat-btn">在线客服</button>
    <a href="tel:4001234567"><button class="button">拨打热线</button></a>
  </section>

  <section class="section" id="youth">
    <h2>未成年人保护</h2>
    <div class="card-grid">
      <div class="card"><h3>家长监护设置</h3><p>引导家长为孩子设定使用规范，查看操作指南。</p><button class="button">立即查看</button></div>
      <div class="card"><h3>实名认证与限额说明</h3><p>说明未成年用户实名认证流程及充值使用限额。</p><button class="button">了解详情</button></div>
      <div class="card"><h3>志愿辅导与活动</h3><p>参与腾讯联合社会组织提供的青少年活动与辅导。</p><button class="button">参与报名</button></div>
    </div>
  </section>
</main>

<footer>
  <div class="footer-links">
    <a href="#terms">服务协议</a> │
    <a href="#privacy">隐私指引</a> │
    <a href="#sitemap">网站地图</a> │
    <a href="#company">关于我们</a>
  </div>
  <p>粤网文[2023]2882‑203号 粤ICP备 号 … © 1998‑2025 腾讯公司 版权所有</p>
</footer>

<!-- 聊天弹窗 -->
<div id="chat-box">
  <div id="chat-header">在线客服 <span id="close-chat" style="float:right;cursor:pointer;">✖</span></div>
  <div id="chat-messages">您好，有什么可以帮您？</div>
  <div id="chat-input">
    <input type="text" id="chat-input-field" placeholder="输入消息...">
    <button id="chat-send">发送</button>
  </div>
</div>

<script>
// 移动导航
document.querySelector('.hamburger').addEventListener('click', ()=>{
  document.querySelector('.nav-menu').classList.toggle('active');
});

// 聊天弹窗
const chatBox = document.getElementById('chat-box');
const openChat = document.getElementById('open-chat');
const openChatBtn = document.getElementById('open-chat-btn');
const closeChat = document.getElementById('close-chat');
const chatMessages = document.getElementById('chat-messages');
const chatInput = document.getElementById('chat-input-field');
const chatSend = document.getElementById('chat-send');

function appendChat(role, text){
  const div = document.createElement('div');
  div.style.marginTop = '5px';
  div.textContent = (role==='user'?'您: ':'客服: ')+text;
  if(role==='agent') div.style.color = '#0078d7';
  chatMessages.appendChild(div);
  chatMessages.scrollTop = chatMessages.scrollHeight;
}

function showChat(){ chatBox.style.display='flex'; chatInput.focus(); }
openChat.addEventListener('click', showChat);
openChatBtn.addEventListener('click', showChat);
closeChat.addEventListener('click', ()=>{ chatBox.style.display='none'; });

chatSend.addEventListener('click', ()=>{
  const val = chatInput.value.trim();
  if(!val) return;
  appendChat('user', val);
  chatInput.value='';
  setTimeout(()=>{ appendChat('agent','请稍等，我们正在处理中…'); }, 500);
});
chatInput.addEventListener('keydown', e=>{ if(e.key==='Enter'){ chatSend.click(); } });

// FAQ 搜索按钮
document.getElementById('faqSearchBtn').addEventListener('click', ()=>{
  const q = document.getElementById('faqSearch').value.trim();
  if(!q){ alert('请输入关键词'); return; }
  alert('正在搜索：“'+q+'”（示例页面）');
});
</script>

</body>
</html>
