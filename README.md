<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>UniRent — Thuê đồ sinh viên P2P</title>
<style>
:root{--bg:#f7f7f5;--ink:#151515;--muted:#737373;--line:#e8e8e3;--accent:#6d5dfc;--accent2:#edeaff;--card:#fff;--green:#16845b}
*{box-sizing:border-box}body{margin:0;font-family:Inter,ui-sans-serif,system-ui,-apple-system,BlinkMacSystemFont,"Segoe UI",sans-serif;color:var(--ink);background:var(--bg)}
button,input,select{font:inherit}.container{max-width:1180px;margin:auto;padding:0 24px}
header{position:sticky;top:0;z-index:20;background:rgba(247,247,245,.9);backdrop-filter:blur(14px);border-bottom:1px solid var(--line)}
.nav{height:72px;display:flex;align-items:center;justify-content:space-between;gap:24px}.logo{font-weight:900;font-size:23px;letter-spacing:-1px}.logo span{color:var(--accent)}
.navlinks{display:flex;gap:24px;color:#555;font-size:14px}.navlinks a{text-decoration:none;color:inherit}.actions{display:flex;gap:9px;align-items:center}
.btn{border:1px solid #ddd;background:#fff;padding:10px 15px;border-radius:12px;cursor:pointer;font-weight:700}.btn.primary{background:var(--ink);color:#fff;border-color:var(--ink)}.btn.purple{background:var(--accent);color:white;border-color:var(--accent)}
.hero{padding:78px 0 54px;display:grid;grid-template-columns:1.05fr .95fr;gap:50px;align-items:center}.eyebrow{display:inline-flex;background:var(--accent2);color:#5648dc;padding:8px 12px;border-radius:99px;font-size:13px;font-weight:800}
h1{font-size:clamp(42px,6vw,72px);line-height:.98;letter-spacing:-4px;margin:18px 0}.hero p{font-size:18px;color:var(--muted);line-height:1.6;max-width:620px}.hero-actions{display:flex;gap:10px;margin-top:25px;flex-wrap:wrap}
.visual{background:#171717;border-radius:30px;padding:22px;min-height:420px;position:relative;overflow:hidden;color:#fff}.visual:before{content:"";position:absolute;width:300px;height:300px;background:#6d5dfc;border-radius:50%;filter:blur(35px);right:-70px;top:-80px;opacity:.8}
.mock{position:absolute;inset:48px 28px 28px;background:#f7f7f5;color:#111;border-radius:22px;padding:18px;transform:rotate(2deg);box-shadow:0 25px 60px #0005}.mocktop{display:flex;justify-content:space-between;font-size:12px;font-weight:800}.mocktitle{font-size:28px;font-weight:900;margin:35px 0 14px}.mockgrid{display:grid;grid-template-columns:1fr 1fr;gap:10px}.mini{background:#fff;border:1px solid #e9e9e9;border-radius:14px;padding:12px}.mini .pic{height:100px;border-radius:10px;background:linear-gradient(135deg,#dfe5ff,#f5dce9);display:grid;place-items:center;font-size:38px;overflow:hidden}.mini .pic img{width:100%;height:100%;object-fit:cover;display:block}.mini:nth-child(2) .pic{background:linear-gradient(135deg,#dff4e8,#fff0c9)}

.section{padding:45px 0}.section-head{display:flex;justify-content:space-between;align-items:end;margin-bottom:20px}.section h2{font-size:30px;letter-spacing:-1.5px;margin:0}.muted{color:var(--muted)}
.searchbar{background:#fff;border:1px solid var(--line);padding:10px;border-radius:18px;display:flex;gap:8px;margin:10px 0 25px}.searchbar input{flex:1;border:0;outline:0;padding:10px;font-size:16px;background:transparent}.searchbar select{border:0;background:#f4f4f2;border-radius:10px;padding:0 12px;outline:0}
.chips{display:flex;gap:8px;overflow:auto;padding-bottom:8px}.chip{border:1px solid #ddd;background:#fff;padding:8px 13px;border-radius:99px;cursor:pointer;white-space:nowrap}.chip.active{background:var(--ink);color:#fff;border-color:var(--ink)}
.grid{display:grid;grid-template-columns:repeat(4,1fr);gap:16px}.card{background:var(--card);border:1px solid var(--line);border-radius:18px;overflow:hidden;transition:.2s}.card:hover{transform:translateY(-3px);box-shadow:0 14px 35px #0000000d}.photo{height:210px;display:grid;place-items:center;font-size:70px;position:relative}.tag{position:absolute;left:12px;top:12px;background:#fff;padding:6px 9px;border-radius:8px;font-size:11px;font-weight:900}.heart{position:absolute;right:12px;top:12px;border:0;background:#fff;border-radius:50%;width:34px;height:34px;cursor:pointer}.cardbody{padding:15px}.title{font-weight:850;font-size:16px}.price{font-weight:900;margin-top:8px}.price span{font-weight:500;color:var(--muted);font-size:12px}.meta{color:var(--muted);font-size:12px;margin-top:7px}.owner{display:flex;align-items:center;gap:8px;margin-top:13px;font-size:12px}.avatar{width:26px;height:26px;border-radius:50%;background:#eee;display:grid;place-items:center;font-size:13px}

.how{display:grid;grid-template-columns:repeat(3,1fr);gap:14px}.step{padding:22px;border:1px solid var(--line);background:#fff;border-radius:18px}.num{width:34px;height:34px;border-radius:10px;background:var(--accent2);color:#5748de;display:grid;place-items:center;font-weight:900}.step h3{margin-bottom:7px}.step p{color:var(--muted);line-height:1.55;font-size:14px}
.cta{margin:35px 0 70px;background:#171717;color:#fff;border-radius:25px;padding:38px;display:flex;justify-content:space-between;align-items:center;gap:25px}.cta h2{font-size:34px;margin:0 0 8px;letter-spacing:-1.5px}.cta p{color:#bbb;margin:0}
footer{border-top:1px solid var(--line);padding:30px 0 50px;color:#777;font-size:13px}

.modal{display:none;position:fixed;inset:0;background:#0007;z-index:50;padding:20px;align-items:center;justify-content:center}.modal.show{display:flex}.modalbox{background:#fff;border-radius:22px;padding:25px;max-width:520px;width:100%;box-shadow:0 30px 80px #0005}.modalhead{display:flex;justify-content:space-between;align-items:center}.close{border:0;background:#f2f2f0;border-radius:9px;width:34px;height:34px;cursor:pointer}.form{display:grid;gap:12px;margin-top:18px}.form input,.form textarea,.form select{width:100%;border:1px solid #ddd;border-radius:11px;padding:12px;outline:0}.form textarea{min-height:90px;resize:vertical}.toast{position:fixed;bottom:22px;left:50%;transform:translateX(-50%);background:#171717;color:#fff;padding:12px 18px;border-radius:99px;display:none;z-index:100}.toast.show{display:block}
@media(max-width:900px){.hero{grid-template-columns:1fr}.grid{grid-template-columns:repeat(2,1fr)}.navlinks{display:none}.how{grid-template-columns:1fr}.cta{flex-direction:column;align-items:flex-start}}
@media(max-width:560px){.container{padding:0 16px}.grid{grid-template-columns:1fr}.hero{padding-top:50px}.visual{min-height:360px}.searchbar{flex-wrap:wrap}.searchbar select{height:42px}.searchbar input{min-width:160px}}

.safe-grid{display:grid;grid-template-columns:1fr 1fr;gap:48px;align-items:start}.safe-heading{display:flex;align-items:center;gap:14px;margin-bottom:22px}.safe-heading h3{font-size:28px;letter-spacing:-.8px;margin:0}.safe-icon{width:58px;height:58px;background:#fff;border:1px solid #f0efeb;border-radius:16px;display:grid;place-items:center;font-size:27px;box-shadow:0 3px 8px #00000005}.match-flow{display:flex;align-items:center;justify-content:space-around;background:#fff;border:1px solid var(--line);border-radius:18px;padding:20px 12px;box-shadow:0 3px 8px #00000004}.match-flow>div{display:flex;flex-direction:column;align-items:center;gap:10px;min-width:58px}.flow-num{width:54px;height:54px;border-radius:50%;background:#f47700;color:#fff;display:grid;place-items:center;font-weight:900;font-size:21px}.match-flow b{font-size:17px}.match-flow i{height:2px;background:#f5c79f;flex:1;position:relative;max-width:90px}.match-flow i:after{content:"";position:absolute;right:0;top:-4px;width:8px;height:8px;border-top:2px solid #f5c79f;border-right:2px solid #f5c79f;transform:rotate(45deg)}.match-label{margin:26px 0 15px;font-size:21px}.match-grid{display:grid;grid-template-columns:1fr 1fr;gap:14px}.match-card{background:#fff;border:1px solid var(--line);border-radius:16px;padding:20px;min-height:112px;box-shadow:0 3px 8px #00000004}.match-card b{font-size:17px}.match-card em{font-style:normal;color:#f47700;font-size:24px;margin-right:7px}.match-card p,.safe-row p{margin:7px 0 0;color:var(--muted);font-size:14px;line-height:1.5}.safe-list{display:grid;gap:13px}.safe-row{display:flex;align-items:center;gap:18px;background:#fff;border:1px solid var(--line);border-radius:16px;padding:18px 20px;box-shadow:0 3px 8px #00000004}.safe-row>span{width:48px;height:48px;flex:0 0 48px;border-radius:50%;display:grid;place-items:center;background:#f8f8f3;color:#55a765;font-weight:900;font-size:20px}.safe-row b{font-size:17px}.safe-row p{margin-top:3px}.safe-note{margin-top:14px;border:2px solid #5bad69;border-radius:15px;color:#55a765;text-align:center;padding:13px 16px;font-weight:800;line-height:1.45}@media(max-width:800px){.safe-grid{grid-template-columns:1fr;gap:32px}.safe-heading h3{font-size:25px}.match-card{padding:16px}.safe-row{padding:15px}}

.account-pill{display:flex;align-items:center;gap:8px;background:#fff;border:1px solid var(--line);border-radius:12px;padding:7px 10px;font-size:13px;font-weight:750}
.account-pill .avatar{background:var(--accent2);color:var(--accent)}
.form small.error{color:#c62828}.form small.hint{color:var(--muted);line-height:1.45}
.empty-state{grid-column:1/-1;background:#fff;border:1px dashed #ddd;border-radius:16px;padding:35px;text-align:center;color:var(--muted)}
.credits-wrap{text-align:center;display:grid;gap:12px}.credits-names,.credits-bottom{display:flex;justify-content:center;gap:18px;flex-wrap:wrap}.credits-names{font-weight:700;color:#444}.credits-bottom{font-size:11px;letter-spacing:1.5px}
@media(max-width:560px){.actions{gap:5px}.actions .btn{padding:8px 10px;font-size:12px}.account-pill{max-width:100px;overflow:hidden;text-overflow:ellipsis;white-space:nowrap}}
</style>
</head>
<body>
<header><div class="container nav">
  <div class="logo">Uni<span>Rent</span></div>
  <nav class="navlinks"><a href="#browse">Khám phá</a><a href="#safe-rental">Safe Rental</a><a href="#how">Cách hoạt động</a><a href="#sell">Cho thuê</a><a href="#" onclick="event.preventDefault();openModal('rent')">Đăng món đồ</a></nav>
  <div class="actions" id="accountActions"><button class="btn" onclick="openModal('login')">Đăng nhập</button><button class="btn primary" onclick="openModal('register')">Đăng ký</button></div>
</div></header>

<main>
<section class="container hero">
  <div><span class="eyebrow">P2P rental dành riêng cho sinh viên</span>
    <h1>Thuê đồ thông minh.<br><span style="color:#6d5dfc">Tiết kiệm hơn.</span></h1>
    <p>UniRent kết nối sinh viên có đồ chưa dùng với sinh viên đang cần — từ máy ảnh, máy chiếu đến áo dài, sách và đồ cắm trại.</p>
    <div class="hero-actions"><a class="btn primary" href="#browse" style="text-decoration:none">Khám phá đồ thuê →</a><button class="btn" onclick="openModal('rent')">💰 Cho thuê & kiếm thêm</button></div>
  </div>
  <div class="visual"><div class="mock"><div class="mocktop"><span>UniRent</span><span>📍 TP.HCM</span></div><div class="mocktitle">Đồ hot gần bạn</div><div class="mockgrid">
    <div class="mini"><div class="pic"><img src="https://i.pinimg.com/1200x/19/6a/0d/196a0d47a782443c8b36bcd6070b843c.jpg" alt="Fujifilm X-A7" onerror="this.style.display='none'"></div><b>Fujifilm X-A7</b><br><small>120k/ngày</small></div>
    <div class="mini"><div class="pic"><img src="https://i.pinimg.com/736x/82/84/e3/8284e305146ef9e547bb8c473168009b.jpg" alt="Máy chiếu mini" onerror="this.style.display='none'"></div><b>Máy chiếu mini</b><br><small>70k/ngày</small></div>
  </div></div></div>
</section>

<section class="section container" id="browse">
  <div class="section-head"><div><h2>Đồ đang được thuê</h2><div class="muted">Lựa chọn từ cộng đồng sinh viên</div></div><span id="count" class="muted"></span></div>
  <div class="searchbar"><input id="search" placeholder="Tìm máy ảnh, sách, áo dài..." oninput="render()"><select id="sort" onchange="render()"><option value="new">Mới nhất</option><option value="low">Giá thấp nhất</option><option value="high">Giá cao nhất</option></select></div>
  <div class="chips">
    <button class="chip active" onclick="filterCat('Tất cả',this)">Tất cả</button><button class="chip" onclick="filterCat('Công nghệ',this)">💻 Công nghệ</button><button class="chip" onclick="filterCat('Học tập',this)">📚 Học tập</button><button class="chip" onclick="filterCat('Sự kiện',this)">👗 Sự kiện</button><button class="chip" onclick="filterCat('Lifestyle',this)">🏕️ Lifestyle</button>
  </div>
  <div class="grid" id="products"></div>
</section>

<section class="section container" id="safe-rental"><div class="section-head"><div><h2>Why Are We Different?</h2><div class="muted">Thuê đồ an tâm hơn — cho cả người thuê và chủ đồ.</div></div></div><div class="safe-grid"><div class="safe-column"><div class="safe-heading"><span class="safe-icon">🤖</span><h3>Smart Matching</h3></div><div class="match-flow"><div><span class="flow-num">1</span><b>Need</b></div><i></i><div><span class="flow-num">2</span><b>Match</b></div><i></i><div><span class="flow-num">3</span><b>Rent</b></div></div><h3 class="match-label">Matches based on:</h3><div class="match-grid"><div class="match-card"><b><em>•</em> Item</b><p>Connects the right item</p></div><div class="match-card"><b><em>•</em> Location</b><p>With the right person</p></div><div class="match-card"><b><em>•</em> Rental time</b><p>At the right time</p></div><div class="match-card"><b><em>•</em> Budget</b><p>At the right price</p></div></div></div><div class="safe-column"><div class="safe-heading"><span class="safe-icon">🛡️</span><h3>Safe Rental</h3></div><div class="safe-list"><div class="safe-row"><span>1</span><div><b>Deposit</b><p>Ensures commitment and item safety</p></div></div><div class="safe-row"><span>2</span><div><b>Rating system</b><p>Builds trust through community feedback</p></div></div><div class="safe-row"><span>3</span><div><b>Secure payment</b><p>Protects financial transactions</p></div></div><div class="safe-row"><span>4</span><div><b>Transaction protection</b><p>Safeguards the rental process</p></div></div></div><div class="safe-note">Together, these elements reduce uncertainty for both renters and owners.</div></div></div></section>
<section class="section container" id="how"><div class="section-head"><div><h2>Thuê trong 3 bước</h2><div class="muted">Không cần mua món đồ chỉ dùng vài lần.</div></div></div>
<div class="how"><div class="step"><div class="num">1</div><h3>Tìm đồ</h3><p>Lọc theo danh mục, giá và khu vực trường học để tìm món phù hợp.</p></div><div class="step"><div class="num">2</div><h3>Đặt thuê</h3><p>Chọn thời gian, nhắn chủ đồ và thống nhất điểm nhận/trả.</p></div><div class="step"><div class="num">3</div><h3>Dùng & trả</h3><p>Kiểm tra tình trạng, sử dụng và trả đúng thời gian. Đánh giá sau giao dịch.</p></div></div></section>

<section class="container" id="sell"><div class="cta"><div><h2>Đồ bạn ít dùng?</h2><p>Biến nó thành thu nhập thêm cùng cộng đồng sinh viên.</p></div><button class="btn" onclick="openModal('rent')">Đăng món đồ miễn phí →</button></div></section>
</main>
<footer><div class="container credits-wrap"><div class="credits-top"><span>© 2026 UniRent · P2P rental cho sinh viên · TP.HCM</span></div><div class="credits-names"><span>Lekhyna_</span><span>Danh_</span><span>Kim Anh_</span><span>Quyên_</span><span>Thịnh</span></div><div class="credits-bottom"><span>FLUX MEDIA ·</span><span>GES2603</span></div></div></footer>

<div class="modal" id="modal"><div class="modalbox"><div class="modalhead"><h2 id="modalTitle">Đăng món đồ</h2><button class="close" onclick="closeModal()">×</button></div><div id="modalContent"></div></div></div>
<div class="toast" id="toast"></div>

<script>
const defaultData=[
 {id:"seed-1",name:"Fujifilm X-A7",cat:"Công nghệ",price:120,icon:"📷",image:"https://i.pinimg.com/236x/d6/c0/9c/d6c09c281061b2e14bad23de06d3e23e.jpg",bg:"linear-gradient(135deg,#e9e1ff,#ffe9dc)",owner:"Minh Anh",school:"ĐH Văn Lang"},
 {id:"seed-2",name:"Máy chiếu mini",cat:"Công nghệ",price:70,icon:"📽️",image:"https://i.pinimg.com/736x/82/84/e3/8284e305146ef9e547bb8c473168009b.jpg",bg:"linear-gradient(135deg,#dff4e8,#fff0c9)",owner:"Quốc Bảo",school:"UEH"},
 {id:"seed-3",name:"Máy tính Casio FX-580",cat:"Học tập",price:20,icon:"🧮",image:"https://i.pinimg.com/736x/f5/e9/30/f5e930c873d2121bc6535376da70ed44.jpg",bg:"linear-gradient(135deg,#e9f0ff,#e9e9e9)",owner:"Thảo",school:"HUTECH"},
 {id:"seed-4",name:"Áo dài trắng",cat:"Sự kiện",price:80,icon:"👗",image:"https://i.pinimg.com/1200x/7a/89/4a/7a894ab8b13fce9b2614071c86b0865d.jpg",bg:"linear-gradient(135deg,#fff,#eadfff)",owner:"Linh",school:"ĐH Kinh tế"},
 {id:"seed-5",name:"Lều 2 người",cat:"Lifestyle",price:100,icon:"⛺",image:"https://i.pinimg.com/736x/c4/b8/f6/c4b8f615fcfcd3e19bebb67f74a1bdc9.jpg",bg:"linear-gradient(135deg,#e6f4e8,#dcecff)",owner:"Khang",school:"Tôn Đức Thắng"},
 {id:"seed-6",name:"GoPro Hero 10",cat:"Công nghệ",price:150,icon:"🎥",image:"https://i.pinimg.com/236x/72/1f/77/721f77a3d4db425d60350c4d1460d157.jpg",bg:"linear-gradient(135deg,#f4e2e2,#e2eaff)",owner:"Duy",school:"RMIT"},
 {id:"seed-7",name:"Micro thu âm",cat:"Công nghệ",price:90,icon:"🎙️",image:"https://i.pinimg.com/1200x/18/c1/17/18c117f091df53c6cdcaa1f8bd095668.jpg",bg:"linear-gradient(135deg,#eee,#dce8ff)",owner:"Phúc",school:"FPT"},
 {id:"seed-8",name:"Sách IELTS 15",cat:"Học tập",price:15,icon:"📚",image:"https://sachngoaingugiare.com/wp-content/uploads/2021/05/elts15-2.jpg",bg:"linear-gradient(135deg,#fff1d8,#e8efff)",owner:"Ngọc",school:"USSH"}];
const store={
 get(key,fallback){try{const v=localStorage.getItem("unirent_"+key);return v===null?fallback:JSON.parse(v)}catch(e){return fallback}},
 set(key,value){try{localStorage.setItem("unirent_"+key,JSON.stringify(value));return true}catch(e){return false}}
};
let data=store.get("listings",defaultData);
let users=store.get("users",[]);
let currentUser=store.get("session",null);
let favorites=store.get("favorites",[]);
let bookings=store.get("bookings",[]);
let category="Tất cả";
function saveListings(){store.set("listings",data)}
function safe(s){return String(s??"").replace(/[&<>"']/g,c=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"}[c]))}
function requireLogin(){if(!currentUser){openModal("login");toast("Bạn cần đăng nhập trước nhé.");return false}return true}
function updateAccountUI(){
 const el=document.getElementById("accountActions");if(!el)return;
 if(currentUser){el.innerHTML=`<span class="account-pill"><span class="avatar">${safe((currentUser.name||"U").trim().charAt(0).toUpperCase())}</span>${safe(currentUser.name)}</span><button class="btn" onclick="openModal('myItems')">Tin của tôi</button><button class="btn" onclick="openModal('bookingList')">Yêu cầu thuê</button><button class="btn" onclick="logout()">Đăng xuất</button>`}
 else el.innerHTML=`<button class="btn" onclick="openModal('login')">Đăng nhập</button><button class="btn primary" onclick="openModal('register')">Đăng ký</button>`;
}
function render(){
 const q=(document.getElementById("search")?.value||"").toLowerCase().trim(),sort=document.getElementById("sort")?.value||"new";
 let arr=data.filter(x=>(category==="Tất cả"||x.cat===category)&&`${x.name} ${x.cat} ${x.school} ${x.owner}`.toLowerCase().includes(q));
 if(sort==="low")arr.sort((a,b)=>a.price-b.price);else if(sort==="high")arr.sort((a,b)=>b.price-a.price);else arr.sort((a,b)=>(b.createdAt||0)-(a.createdAt||0));
 document.getElementById("count").textContent=arr.length+" món";
 document.getElementById("products").innerHTML=arr.length?arr.map(x=>`<article class="card"><div class="photo" style="background:${x.bg||"linear-gradient(135deg,#eee,#e9e1ff)"}"><span class="tag">${safe(x.cat)}</span><button class="heart" aria-label="Yêu thích" onclick="like('${safe(x.id)}')">${favorites.includes(x.id)?"♥":"♡"}</button>${x.image?`<img src="${safe(x.image)}" alt="${safe(x.name)}" loading="lazy" style="width:100%;height:100%;object-fit:cover;position:absolute;inset:0" onerror="this.style.display='none'">`:safe(x.icon||"📦")}</div><div class="cardbody"><div class="title">${safe(x.name)}</div><div class="price">${(Number(x.price)*1000).toLocaleString("vi-VN")}đ <span>/ ngày</span></div><div class="meta">📍 ${safe(x.school||"Chưa cập nhật")}</div><div class="owner"><span class="avatar">${safe((x.owner||"U").charAt(0))}</span>${safe(x.owner||"Thành viên UniRent")} · ⭐ 4.9</div><button class="btn primary" style="width:100%;margin-top:13px" onclick="book('${safe(x.id)}')">Thuê món này</button></div></article>`).join(""):`<div class="empty-state"><div style="font-size:32px">🔎</div><b>Chưa tìm thấy món đồ phù hợp</b><p>Thử từ khóa khác hoặc chọn danh mục “Tất cả”.</p></div>`;
}
function filterCat(c,el){category=c;document.querySelectorAll(".chip").forEach(x=>x.classList.remove("active"));el.classList.add("active");render()}
function like(id){if(!requireLogin())return;favorites=favorites.includes(id)?favorites.filter(x=>x!==id):[...favorites,id];store.set("favorites",favorites);render();toast(favorites.includes(id)?"Đã thêm vào yêu thích ♥":"Đã bỏ khỏi yêu thích")}
function field(id){return document.getElementById(id)?.value?.trim()||""}
function setModal(title,content){document.getElementById("modalTitle").textContent=title;document.getElementById("modalContent").innerHTML=content;document.getElementById("modal").classList.add("show")}
function openModal(type){
 if(type==="register"){
  setModal("Tạo tài khoản UniRent",`<form class="form" onsubmit="register(event)"><input id="regName" placeholder="Họ và tên" autocomplete="name" required maxlength="80"><input id="regEmail" type="email" placeholder="Email" autocomplete="email" required maxlength="160"><input id="regSchool" placeholder="Trường đại học / cao đẳng" required maxlength="120"><input id="regPassword" type="password" placeholder="Mật khẩu (ít nhất 8 ký tự)" autocomplete="new-password" minlength="8" required><input id="regConfirm" type="password" placeholder="Nhập lại mật khẩu" autocomplete="new-password" minlength="8" required><small id="regError" class="error" role="alert"></small><button class="btn purple" type="submit">Tạo tài khoản</button><small class="hint">Bản thử nghiệm lưu trên trình duyệt này, chưa đồng bộ giữa các thiết bị.</small><button type="button" class="btn" onclick="openModal('login')">Đã có tài khoản? Đăng nhập</button></form>`);
 }else if(type==="login"){
  setModal("Đăng nhập UniRent",`<form class="form" onsubmit="login(event)"><input id="loginEmail" type="email" placeholder="Email" autocomplete="email" required><input id="loginPassword" type="password" placeholder="Mật khẩu" autocomplete="current-password" required><small id="loginError" class="error" role="alert"></small><button class="btn primary" type="submit">Đăng nhập</button><small class="hint">Dùng email và mật khẩu đã đăng ký trên trình duyệt này.</small><button type="button" class="btn" onclick="openModal('register')">Chưa có tài khoản? Đăng ký</button></form>`);
 }else if(type==="myItems"){
  if(!requireLogin())return;
  const mine=data.filter(x=>x.userEmail===currentUser.email);
  setModal("Tin cho thuê của tôi",mine.length?`<div class="form">${mine.map(x=>`<div class="step"><b>${safe(x.name)}</b><p>${(Number(x.price)*1000).toLocaleString("vi-VN")}đ/ngày · ${safe(x.cat)}</p><button class="btn" onclick="deleteListing('${safe(x.id)}')">Xóa tin</button></div>`).join("")}</div>`:`<div class="form"><p>Bạn chưa đăng món đồ nào.</p><button class="btn purple" onclick="openModal('rent')">Đăng món đồ đầu tiên</button></div>`);
 }else if(type==="bookingList"){
  if(!requireLogin())return;
  const mine=bookings.filter(b=>b.renterEmail===currentUser.email||data.some(x=>x.id===b.itemId&&x.userEmail===currentUser.email));
  setModal("Yêu cầu thuê của tôi",mine.length?`<div class="form">${mine.map(b=>{const it=data.find(x=>x.id===b.itemId);return `<div class="step"><b>${safe(it?.name||"Món đồ đã xóa")}</b><p>${safe(b.renterName)} · ${safe(b.start)} → ${safe(b.end)}</p><p>Trạng thái: ${safe(b.status)}</p>${it?.userEmail===currentUser.email?`<button class="btn" onclick="setBookingStatus('${safe(b.id)}','Đã xác nhận')">Xác nhận thuê</button> <button class="btn" onclick="setBookingStatus('${safe(b.id)}','Từ chối')">Từ chối</button>`:""}</div>`}).join("")}</div>`:`<div class="form"><p>Chưa có yêu cầu thuê nào.</p></div>`);
 }else{
  if(type==="rent"&&!currentUser){openModal("login");toast("Đăng nhập để đăng tin cho thuê.");return}
  setModal("Đăng món đồ cho thuê",`<form class="form" onsubmit="createListing(event)"><input id="itemName" placeholder="Tên món đồ" required maxlength="100"><select id="itemCat" required><option value="">Chọn danh mục</option><option>Công nghệ</option><option>Học tập</option><option>Sự kiện</option><option>Lifestyle</option></select><input id="itemPrice" type="number" min="1" max="1000000" placeholder="Giá thuê / ngày (nghìn VNĐ)" required><input id="itemSchool" placeholder="Khu vực / trường" required maxlength="120"><input id="itemImage" type="url" placeholder="Link ảnh món đồ (không bắt buộc)"><textarea id="itemDesc" placeholder="Mô tả tình trạng, phụ kiện đi kèm..." maxlength="1000"></textarea><small id="itemError" class="error" role="alert"></small><button class="btn purple" type="submit">Đăng tin miễn phí</button></form>`);
 }
}
function register(event){
 event.preventDefault();const name=field("regName"),email=field("regEmail").toLowerCase(),school=field("regSchool"),password=document.getElementById("regPassword").value,confirm=document.getElementById("regConfirm").value,err=document.getElementById("regError");
 if(password.length<8){err.textContent="Mật khẩu cần ít nhất 8 ký tự.";return}
 if(password!==confirm){err.textContent="Mật khẩu nhập lại chưa khớp.";return}
 if(users.some(u=>u.email===email)){err.textContent="Email này đã được đăng ký. Hãy đăng nhập.";return}
 // Prototype only: use a secure authentication backend before publishing for real users.
 users.push({name,email,school,password});store.set("users",users);currentUser={name,email,school};store.set("session",currentUser);updateAccountUI();closeModal();toast("Tạo tài khoản thành công!");render();
}
function login(event){
 event.preventDefault();const email=field("loginEmail").toLowerCase(),password=document.getElementById("loginPassword").value,err=document.getElementById("loginError"),user=users.find(u=>u.email===email&&u.password===password);
 if(!user){err.textContent="Email hoặc mật khẩu không đúng, hoặc bạn chưa đăng ký trên trình duyệt này.";return}
 currentUser={name:user.name,email:user.email,school:user.school};store.set("session",currentUser);updateAccountUI();closeModal();toast("Đăng nhập thành công!");render();
}
function logout(){currentUser=null;store.set("session",null);updateAccountUI();render();toast("Bạn đã đăng xuất.")}
function createListing(event){
 event.preventDefault();if(!requireLogin())return;
 const name=field("itemName"),cat=field("itemCat"),price=Number(field("itemPrice")),school=field("itemSchool"),image=field("itemImage"),desc=field("itemDesc");
 if(!name||!cat||!Number.isFinite(price)||price<=0||!school){document.getElementById("itemError").textContent="Vui lòng kiểm tra các thông tin bắt buộc.";return}
 const icons={"Công nghệ":"💻","Học tập":"📚","Sự kiện":"👗","Lifestyle":"🏕️"};
 data.unshift({id:"item-"+Date.now(),name,cat,price,icon:icons[cat]||"📦",image:image||"",bg:"linear-gradient(135deg,#eee8ff,#e4f5ed)",owner:currentUser.name,school,description:desc,userEmail:currentUser.email,createdAt:Date.now()});
 saveListings();closeModal();render();toast("Đăng tin thành công!");document.getElementById("browse").scrollIntoView({behavior:"smooth"});
}
function deleteListing(id){
 if(!requireLogin())return;const item=data.find(x=>x.id===id);if(!item||item.userEmail!==currentUser.email){toast("Bạn chỉ có thể xóa tin của mình.");return}
 data=data.filter(x=>x.id!==id);saveListings();render();openModal("myItems");toast("Đã xóa tin đăng.");
}
function book(id){
 if(!requireLogin())return;const item=data.find(x=>x.id===id);if(!item)return;
 if(item.userEmail===currentUser.email){toast("Bạn không thể tự đặt thuê món đồ của mình.");return}
 setModal("Đặt thuê — "+item.name,`<form class="form" onsubmit="submitBooking(event,'${safe(item.id)}')"><p><b>${(Number(item.price)*1000).toLocaleString("vi-VN")}đ/ngày</b> · Chủ đồ: ${safe(item.owner)}</p><label for="bookStart">Ngày nhận đồ</label><input id="bookStart" type="date" min="${new Date().toISOString().slice(0,10)}" required><label for="bookEnd">Ngày trả đồ</label><input id="bookEnd" type="date" min="${new Date().toISOString().slice(0,10)}" required><textarea id="bookMessage" placeholder="Tin nhắn cho chủ đồ (không bắt buộc)" maxlength="500"></textarea><small id="bookError" class="error" role="alert"></small><button class="btn primary" type="submit">Gửi yêu cầu thuê</button></form>`);
}
function submitBooking(event,id){
 event.preventDefault();const start=field("bookStart"),end=field("bookEnd"),message=field("bookMessage"),err=document.getElementById("bookError");
 if(!start||!end||end<start){err.textContent="Ngày trả phải bằng hoặc sau ngày nhận.";return}
 bookings=store.get("bookings",[]);bookings.push({id:"booking-"+Date.now(),itemId:id,renterEmail:currentUser.email,renterName:currentUser.name,start,end,message,status:"Chờ xác nhận",createdAt:Date.now()});store.set("bookings",bookings);closeModal();toast("Đã lưu yêu cầu thuê trên trình duyệt này.");
}
function setBookingStatus(id,status){bookings=store.get("bookings",[]);const b=bookings.find(x=>x.id===id);if(!b)return;const item=data.find(x=>x.id===b.itemId);if(!currentUser||(b.renterEmail!==currentUser.email&&item?.userEmail!==currentUser.email)){toast("Bạn không có quyền cập nhật yêu cầu này.");return}b.status=status;store.set("bookings",bookings);openModal("bookingList");toast("Đã cập nhật yêu cầu thuê.");}
function closeModal(){document.getElementById("modal").classList.remove("show")}
function toast(t){const e=document.getElementById("toast");e.textContent=t;e.classList.add("show");clearTimeout(window.__unirentToast);window.__unirentToast=setTimeout(()=>e.classList.remove("show"),2800)}
document.getElementById("modal").addEventListener("click",e=>{if(e.target.id==="modal")closeModal()});
document.addEventListener("keydown",e=>{if(e.key==="Escape")closeModal()});
updateAccountUI();
render();
</script>
</body>
</html>
