<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Easy Shop | Shop Smarter</title>

<meta name="description" content="Easy Shop - Discover selected products, offers and marketplace links.">
<meta name="theme-color" content="#2874f0">

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900&display=swap" rel="stylesheet">

<style>

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

html{
    scroll-behavior:smooth;
}

body{
    font-family:"Inter",Arial,sans-serif;
    background:var(--bg);
    color:var(--text);
    min-height:100vh;
    overflow-x:hidden;

    --platform:#2874f0;
    --platform2:#1557b0;
    --platform-icon:#2874f0;
    --platform-soft:rgba(40,116,240,.14);

    --bg:#070b14;
    --bg2:#0b1120;
    --card:#101827;
    --card2:#121d2f;
    --text:#ffffff;
    --muted:#9aa7ba;
    --border:rgba(255,255,255,.08);
    --success:#19c37d;
    --danger:#ff5b6e;

    --max:1400px;
}

body[data-platform="flipkart"]{
    --platform:#2874f0;
    --platform2:#1557b0;
    --platform-icon:#2874f0;
    --platform-soft:rgba(40,116,240,.15);
}

body.modal-open{
    overflow:hidden;
}

a{
    color:inherit;
    text-decoration:none;
}

button,
input{
    font-family:inherit;
}

button{
    cursor:pointer;
}

button,
a,
select{
    -webkit-tap-highlight-color:transparent;
}

.game-click{
    animation:gameClickPulse .45s ease;
}

@keyframes gameClickPulse{
    0%{
        filter:brightness(1);
        box-shadow:0 0 0 rgba(25,195,125,0);
    }
    45%{
        filter:brightness(1.35);
        box-shadow:0 0 0 3px var(--platform-soft),0 0 24px var(--platform);
    }
    100%{
        filter:brightness(1);
        box-shadow:0 0 0 rgba(25,195,125,0);
    }
}

button:hover,
a:not(.logo):hover,
select:hover{
    filter:brightness(1.18) saturate(1.2);
    box-shadow:
        0 0 0 2px var(--platform-soft),
        0 0 18px var(--platform);
    text-shadow:0 0 8px rgba(255,255,255,.65);
}

.nav-links > a:hover,
.nav-action:hover,
.login-btn:hover,
.category-btn:hover,
.platform-tab:hover,
.hero-btn:hover,
.add-cart-btn:hover,
.check-price-btn:hover{
    transform:translateY(-3px) scale(1.02);
}

img{
    display:block;
    max-width:100%;
}

.container{
    width:min(100% - 32px,var(--max));
    margin:auto;
}


/* =========================================================
   NAVBAR
========================================================= */

.navbar{
    position:sticky;
    top:0;
    z-index:1000;
    background:rgba(5,8,16,.94);
    backdrop-filter:blur(18px);
    border-bottom:1px solid var(--border);
}

.nav-inner{
    height:76px;
    display:flex;
    align-items:center;
    gap:50px;
}


/* Logo */

.logo{
    display:flex;
    align-items:center;
    gap:10px;
    flex-shrink:0;
}

.logo-mark{
    width:42px;
    height:42px;
    border-radius:13px;
    display:grid;
    place-items:center;
    font-weight:900;
    font-size:19px;
    color:white;
    background:linear-gradient(135deg,var(--platform),var(--platform2));
    box-shadow:0 8px 30px var(--platform-soft);
    transition:.3s;
}

.logo:hover .logo-mark{
    transform:rotate(-7deg) scale(1.05);
}

.logo-text{
    font-size:21px;
    font-weight:900;
    letter-spacing:-.7px;
}

.logo-text span{
    color:var(--platform);
}


/* Navigation */

.nav-links{
    display:flex;
    align-items:center;
    gap:5px;
    margin-left:5px;
}

.nav-links > a,
.platform-menu > button{
    border:0;
    background:transparent;
    color:#dce4f0;
    padding:10px 13px;
    border-radius:9px;
    font-size:14px;
    font-weight:700;
    transition:.25s;
}

.nav-links > a:hover,
.platform-menu > button:hover{
    background:rgba(255,255,255,.06);
    color:#fff;
}


/* Platform dropdown */

.platform-menu{
    position:relative;
}

.platform-menu > button{
    display:flex;
    align-items:center;
    gap:7px;
}

.chevron{
    font-size:11px;
    transition:.25s;
}

.platform-menu:hover .chevron{
    transform:rotate(180deg);
}

.platform-dropdown{
    position:absolute;
    top:calc(100% + 10px);
    left:0;
    width:220px;
    background:#0d1422;
    border:1px solid var(--border);
    border-radius:14px;
    padding:8px;
    box-shadow:0 25px 70px rgba(0,0,0,.45);
    opacity:0;
    visibility:hidden;
    transform:translateY(-7px);
    transition:.25s;
}

.platform-menu:hover .platform-dropdown{
    opacity:1;
    visibility:visible;
    transform:translateY(0);
}

.platform-dropdown button{
    width:100%;
    border:0;
    background:transparent;
    color:#dbe4f2;
    text-align:left;
    padding:12px;
    border-radius:9px;
    font-weight:700;
    display:flex;
    align-items:center;
    gap:10px;
    transition:.2s;
}

.platform-dropdown button:hover{
    background:rgba(255,255,255,.07);
    transform:translateX(3px);
}

.platform-dot{
    width:10px;
    height:10px;
    border-radius:50%;
}

.dot-flipkart{
    background:#2874f0;
}

/* Search */

.search-box{
    flex:1;
    max-width:410px;
    margin-left:auto;
    position:relative;
}

.search-box input{
    width:100%;
    height:43px;
    border:1px solid var(--border);
    outline:none;
    background:#0e1625;
    color:#fff;
    border-radius:11px;
    padding:0 46px 0 15px;
    font-size:13px;
    transition:.25s;
}

.search-box input::placeholder{
    color:#758196;
}

.search-box input:focus{
    border-color:var(--platform);
    box-shadow:0 0 0 3px var(--platform-soft);
}

.search-icon{
    position:absolute;
    right:14px;
    top:50%;
    transform:translateY(-50%);
    color:#8b98ab;
    pointer-events:none;
}


/* Nav actions */

.nav-actions{
    display:flex;
    align-items:center;
    gap:7px;
}

.nav-action{
    position:relative;
    width:42px;
    height:42px;
    border:1px solid var(--border);
    background:#0e1625;
    color:#fff;
    border-radius:11px;
    display:grid;
    place-items:center;
    transition:.25s;
}

.nav-action:hover{
    background:var(--platform);
    transform:translateY(-2px);
}

.cart-count{
    position:absolute;
    right:-5px;
    top:-6px;
    min-width:19px;
    height:19px;
    padding:0 5px;
    border-radius:20px;
    background:#ff405d;
    color:white;
    font-size:10px;
    font-weight:900;
    display:grid;
    place-items:center;
    border:2px solid #050810;
}

.login-btn{
    border:1px solid var(--platform);
    background:var(--platform-soft);
    color:#fff;
    min-height:42px;
    padding:0 16px;
    border-radius:11px;
    font-weight:800;
    transition:.25s;
}

.login-btn:hover{
    background:var(--platform);
    transform:translateY(-2px);
}


.mobile-menu-btn{
    display:none;
    width:42px;
    height:42px;
    border:1px solid var(--border);
    border-radius:10px;
    background:#0e1625;
    color:#fff;
    font-size:19px;
}


/* =========================================================
   HERO SLIDER
========================================================= */

.hero{
    padding:20px 0 0;
}

.slider{
    position:relative;
    width:100%;
    height:460px;
    border-radius:25px;
    overflow:hidden;
    border:1px solid var(--border);
    background:#101827;
    box-shadow:0 30px 90px rgba(0,0,0,.3);
}

.slide{
    position:absolute;
    inset:0;
    opacity:0;
    visibility:hidden;
    transition:opacity .7s ease;
}

.slide.active{
    opacity:1;
    visibility:visible;
}

.slide img{
    width:100%;
    height:100%;
    object-fit:cover;
    filter:brightness(.5) saturate(1.05);
}

.slide::after{
    content:"";
    position:absolute;
    inset:0;
    background:
        linear-gradient(90deg,rgba(0,0,0,.85),rgba(0,0,0,.35),rgba(0,0,0,.15)),
        linear-gradient(0deg,rgba(0,0,0,.65),transparent 55%);
}

.slide-content{
    position:absolute;
    z-index:2;
    left:7%;
    top:50%;
    transform:translateY(-50%);
    max-width:650px;
}

.slide-label{
    display:inline-flex;
    padding:7px 11px;
    border-radius:8px;
    background:var(--platform-soft);
    border:1px solid var(--platform);
    color:#fff;
    font-size:11px;
    font-weight:900;
    letter-spacing:1.2px;
    margin-bottom:15px;
}

.slide h1{
    font-size:clamp(35px,5vw,70px);
    line-height:.98;
    letter-spacing:-3px;
    margin-bottom:17px;
}

.slide h1 span{
    color:var(--platform-icon);
}

.slide p{
    color:#d6deeb;
    line-height:1.7;
    max-width:540px;
    font-size:15px;
}

.hero-btns{
    margin-top:25px;
    display:flex;
    flex-wrap:wrap;
    gap:10px;
}

.hero-btn{
    border:0;
    min-height:46px;
    padding:0 18px;
    border-radius:11px;
    font-weight:900;
    transition:.25s;
}

.hero-primary{
    background:linear-gradient(135deg,var(--platform),var(--platform2));
    color:#fff;
    box-shadow:0 10px 30px var(--platform-soft);
}

.hero-secondary{
    background:rgba(255,255,255,.08);
    border:1px solid rgba(255,255,255,.14);
    color:#fff;
}

.hero-btn:hover{
    transform:translateY(-3px);
}

.slider-arrow{
    position:absolute;
    z-index:5;
    top:50%;
    transform:translateY(-50%);
    width:44px;
    height:44px;
    border:1px solid rgba(255,255,255,.15);
    border-radius:50%;
    background:rgba(0,0,0,.35);
    color:#fff;
    display:grid;
    place-items:center;
    font-size:18px;
    transition:.25s;
}

.slider-arrow:hover{
    background:var(--platform);
}

.slider-prev{
    left:18px;
}

.slider-next{
    right:18px;
}

.slider-dots{
    position:absolute;
    z-index:5;
    bottom:20px;
    left:50%;
    transform:translateX(-50%);
    display:flex;
    gap:7px;
}

.slider-dot{
    width:8px;
    height:8px;
    border:0;
    border-radius:20px;
    background:rgba(255,255,255,.45);
    transition:.3s;
}

.slider-dot.active{
    width:27px;
    background:var(--platform);
}


/* =========================================================
   PLATFORM TABS
========================================================= */

.platform-section{
    padding:30px 0 10px;
}

.section-heading{
    display:flex;
    justify-content:space-between;
    align-items:end;
    gap:20px;
    margin-bottom:17px;
}

.section-heading h2{
    font-size:25px;
    letter-spacing:-1px;
}

.section-heading p{
    margin-top:6px;
    color:var(--muted);
    font-size:13px;
}

.platform-tabs{
    display:grid;
    grid-template-columns:repeat(3,1fr);
    gap:12px;
}

.platform-tab{
    border:1px solid var(--border);
    background:var(--card);
    color:#fff;
    min-height:70px;
    border-radius:15px;
    display:flex;
    align-items:center;
    gap:13px;
    padding:12px 16px;
    transition:.3s;
    text-align:left;
}

.platform-tab:hover{
    transform:translateY(-3px);
    border-color:rgba(255,255,255,.18);
}

.platform-tab.active{
    border-color:var(--platform);
    background:linear-gradient(135deg,var(--platform-soft),rgba(255,255,255,.025));
    box-shadow:0 10px 35px var(--platform-soft);
}

.platform-tab-icon{
    width:43px;
    height:43px;
    border-radius:12px;
    display:grid;
    place-items:center;
    background:rgba(255,255,255,.07);
    font-weight:900;
    font-size:14px;
}

.platform-tab.flipkart .platform-tab-icon{
    color:#2874f0;
}

.platform-tab strong{
    display:block;
    font-size:14px;
}

.platform-tab small{
    color:var(--muted);
    font-size:11px;
}


/* =========================================================
   FEATURES
========================================================= */

.features{
    padding:25px 0 10px;
}

.feature-grid{
    display:grid;
    grid-template-columns:repeat(4,1fr);
    gap:12px;
}

.feature-card{
    padding:20px;
    background:linear-gradient(145deg,var(--card),var(--card2));
    border:1px solid var(--border);
    border-radius:16px;
    transition:.3s;
}

.feature-card:hover{
    transform:translateY(-5px);
    border-color:var(--platform);
    box-shadow:0 15px 45px var(--platform-soft);
}

.feature-icon{
    font-size:23px;
    margin-bottom:11px;
}

.feature-card h3{
    font-size:14px;
    margin-bottom:6px;
}

.feature-card p{
    color:var(--muted);
    font-size:12px;
    line-height:1.6;
}


/* =========================================================
   PRODUCTS
========================================================= */

.products-section{
    padding:55px 0 30px;
}

.product-toolbar{
    display:flex;
    align-items:center;
    justify-content:space-between;
    gap:15px;
    margin-bottom:20px;
}

.result-info{
    color:var(--muted);
    font-size:13px;
}

.result-info strong{
    color:#fff;
}

.sort-select{
    background:#101827;
    color:#fff;
    border:1px solid var(--border);
    border-radius:9px;
    padding:10px 12px;
    outline:none;
}

.category-list{
    display:flex;
    gap:8px;
    flex-wrap:wrap;
    margin-bottom:22px;
}

.category-btn{
    border:1px solid var(--border);
    background:#0e1625;
    color:#bac6d8;
    padding:9px 13px;
    border-radius:9px;
    font-size:12px;
    font-weight:800;
    transition:.25s;
}

.category-btn:hover,
.category-btn.active{
    background:var(--platform);
    border-color:var(--platform);
    color:#fff;
}

.product-grid{
    display:grid;
    grid-template-columns:repeat(4,1fr);
    gap:16px;
}


.product-card{
    position:relative;
    background:linear-gradient(145deg,var(--card),var(--card2));
    border:1px solid var(--border);
    border-radius:17px;
    overflow:hidden;
    transition:.3s;
}

.product-card:hover{
    transform:translateY(-7px);
    border-color:var(--platform);
    box-shadow:0 18px 55px var(--platform-soft);
}

.product-image{
    position:relative;
    height:230px;
    overflow:hidden;
    background:#0b111d;
}

.product-image img{
    width:100%;
    height:100%;
    object-fit:cover;
    transition:.5s;
}

.product-card:hover .product-image img{
    transform:scale(1.07);
}

.discount-badge{
    position:absolute;
    left:12px;
    top:12px;
    background:#19c37d;
    color:#04150e;
    padding:6px 9px;
    border-radius:7px;
    font-size:10px;
    font-weight:900;
    z-index:3;
}

.source-badge{
    position:absolute;
    right:12px;
    top:12px;
    padding:6px 9px;
    border-radius:7px;
    font-size:9px;
    font-weight:900;
    letter-spacing:.5px;
    background:rgba(5,8,16,.85);
    backdrop-filter:blur(8px);
    border:1px solid rgba(255,255,255,.13);
    z-index:3;
}

.source-badge.flipkart{
    color:#6ea3ff;
}

.wishlist-btn{
    position:absolute;
    right:12px;
    bottom:12px;
    width:34px;
    height:34px;
    border-radius:9px;
    border:1px solid rgba(255,255,255,.12);
    background:rgba(5,8,16,.78);
    color:#fff;
    z-index:4;
    transition:.25s;
}

.wishlist-btn:hover{
    background:#ff405d;
}

.product-info{
    padding:16px;
}

.product-name{
    font-size:14px;
    line-height:1.45;
    min-height:41px;
    margin-bottom:9px;
    font-weight:800;
}

.rating-row{
    display:flex;
    align-items:center;
    gap:7px;
    margin-bottom:12px;
}

.rating{
    background:#0f7c4f;
    color:#fff;
    border-radius:6px;
    padding:4px 7px;
    font-size:10px;
    font-weight:900;
}

.rating-stars{
    color:#ffc83d;
    font-size:11px;
    letter-spacing:1px;
}

.review-count{
    color:#7f8ca1;
    font-size:10px;
}

.price-row{
    display:flex;
    align-items:center;
    flex-wrap:wrap;
    gap:8px;
    margin-bottom:6px;
}

.new-price{
    font-size:20px;
    font-weight:900;
}

.old-price{
    color:#68758a;
    font-size:12px;
    text-decoration:line-through;
}

.discount-text{
    color:#19c37d;
    font-size:11px;
    font-weight:900;
}

.delivery{
    color:#8e9caf;
    font-size:10px;
    margin:8px 0 13px;
}

.card-actions{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:8px;
}

.add-cart-btn,
.check-price-btn{
    min-height:39px;
    border-radius:9px;
    font-size:11px;
    font-weight:900;
    transition:.25s;
}

.add-cart-btn{
    border:1px solid var(--border);
    background:#0c1421;
    color:#fff;
}

.add-cart-btn:hover{
    background:rgba(255,255,255,.08);
    border-color:rgba(255,255,255,.2);
}

.check-price-btn{
    border:1px solid rgba(255,255,255,.08);
    color:#fff;
    background:linear-gradient(135deg,var(--platform),var(--platform2));
    box-shadow:0 7px 20px var(--platform-soft);
}

.check-price-btn:hover{
    transform:translateY(-2px);
    filter:brightness(1.1);
}

.price-icon{
    width:20px;
    height:20px;
    display:inline-grid;
    place-items:center;
    color:var(--platform-icon);
    background:#fff;
    border-radius:6px;
    font-size:10px;
    margin-right:5px;
    vertical-align:middle;
}


/* =========================================================
   EMPTY
========================================================= */

.empty-state{
    grid-column:1/-1;
    text-align:center;
    padding:70px 20px;
    background:var(--card);
    border:1px dashed var(--border);
    border-radius:18px;
}

.empty-state .empty-icon{
    font-size:45px;
    margin-bottom:12px;
}

.empty-state h3{
    margin-bottom:6px;
}

.empty-state p{
    color:var(--muted);
    font-size:13px;
}


/* =========================================================
   OFFERS
========================================================= */

.offers-section{
    padding:45px 0 30px;
}

.offer-banner{
    position:relative;
    overflow:hidden;
    min-height:190px;
    border-radius:20px;
    padding:30px;
    background:
        radial-gradient(circle at 80% 20%,var(--platform-soft),transparent 35%),
        linear-gradient(135deg,#111a2b,#0b101c);
    border:1px solid var(--border);
}

.offer-banner::before{
    content:"";
    position:absolute;
    width:230px;
    height:230px;
    right:-70px;
    top:-100px;
    border-radius:50%;
    border:1px solid var(--platform);
    opacity:.25;
}

.offer-banner h2{
    font-size:28px;
    margin-bottom:8px;
}

.offer-banner p{
    color:var(--muted);
    max-width:620px;
    font-size:13px;
    line-height:1.7;
}

.offer-tag{
    display:inline-block;
    margin-bottom:13px;
    padding:6px 9px;
    border-radius:7px;
    background:var(--platform);
    color:#fff;
    font-size:10px;
    font-weight:900;
}

.contact-section{
    padding:30px 0 45px;
}

.contact-card{
    background:var(--card);
    border:1px solid var(--border);
    border-radius:18px;
    padding:28px;
}

.contact-card p{
    color:var(--muted);
    line-height:1.7;
    font-size:13px;
}

.contact-email{
    display:inline-block;
    margin-top:18px;
    color:#6ea3ff;
    font-weight:700;
}


/* =========================================================
   FOOTER
========================================================= */

footer{
    margin-top:25px;
    border-top:1px solid var(--border);
    background:#050810;
}

.footer-main{
    padding:45px 0 30px;
    display:grid;
    grid-template-columns:1.4fr 1fr 1fr 1fr;
    gap:35px;
}

.footer-brand p{
    color:#78869a;
    font-size:12px;
    line-height:1.8;
    max-width:340px;
    margin-top:13px;
}

.footer-col h3{
    font-size:13px;
    margin-bottom:14px;
}

.footer-col a{
    display:block;
    color:#7e8ba0;
    font-size:12px;
    margin-bottom:9px;
    transition:.2s;
}

.footer-col a:hover{
    color:var(--platform);
    transform:translateX(3px);
}

.disclaimer{
    padding:15px 0;
    border-top:1px solid var(--border);
    border-bottom:1px solid var(--border);
    color:#69768a;
    font-size:10px;
    line-height:1.7;
}

.footer-bottom{
    min-height:55px;
    display:flex;
    align-items:center;
    justify-content:space-between;
    gap:15px;
    color:#657286;
    font-size:11px;
}


/* =========================================================
   CART DRAWER
========================================================= */

.overlay{
    position:fixed;
    inset:0;
    z-index:1500;
    background:rgba(0,0,0,.68);
    opacity:0;
    visibi
