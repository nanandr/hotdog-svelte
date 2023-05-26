<script>
  import { onMount, afterUpdate } from "svelte";
  import logo from "./assets/logo.png";
  import banner from "./assets/banner.jpg";
  import circle from "./assets/circle.png"
  import fgBanner from "./assets/fg-banner.png";

  'use strict';
  
  let scroll = {
    x: 0,
    y: 0,
  };
  let mouse = {
    x: 0,
    y: 0,
  };
  let expandNavbar = "";
  onMount(() => {
    window.addEventListener("scroll", handleScroll);
    window.addEventListener("mousemove", handleMouse);
    return () => {
      window.removeEventListener("scroll", handleScroll);
      window.removeEventListener("mousemove", handleMouse);
    };
  });
  function handleScroll() {
    scroll.y = window.scrollY;
  }
  function handleMouse(event){
    mouse.x = event.clientX;
    mouse.y = event.clientY;
  }
  $: {
    expandNavbar = scroll.y > 400 ? "expand" : "";
  }
</script>

<header class={expandNavbar}>
  <nav class="container">
    <div class="navbar-brand" style="background-image: url({logo});" />
    <div class="navbar-content">
      <a href="/#" class="nav-link">Produk</a>
      <a href="/#" class="nav-link">Kontak</a>
      <a href="/#" class="nav-link">Pesan</a>
    </div>
  </nav>
</header>
<div class="banner">
  <div class="container banner-title">
    <h1>HOTDOG ENAK</h1>
  </div>
  <div class="banner-footer">
    <div class="container">
      <a href="/#" class="btn-lg">PESAN SEKARANG</a>
    </div>
  </div>
  <div class="fg-banner container" style="background-image: url({fgBanner});"/>
  <div class="circle-banner" style="background-image: url({circle}); top: {mouse.y - 50}px; left: {mouse.x - 50}px;"></div>
  <div class="banner-bg"></div>
</div>
<main>
  <article class="container">
    <h2>
      Apakah Anda merindukan camilan sempurna yang penuh dengan rasa dan cocok di telapak tangan Anda? Jangan khawatir, Mini Munchers hadir untuk memenuhi keinginan Anda! Ini adalah pengalaman hotdog mini yang sempurna dan akan membuat Anda ketagihan.
      <br>
      Bayangkan merasakan gigitan kecil pada hotdog mini yang penuh dengan kenikmatan. Mini Munchers kami dirancang dengan hati-hati menggunakan sosis berkualitas tinggi yang juicy, dibalut dalam roti empuk berwarna keemasan. Setiap gigitan memberikan ledakan rasa yang akan membawa lidah Anda ke surga makanan.
      <br>
      Tidak peduli apakah Anda sedang mengadakan pesta, menikmati pertemuan keluarga, atau hanya ingin memuaskan keinginan camilan, Mini Munchers adalah pilihan yang sempurna. Camilan ini sangat disukai oleh anak-anak maupun orang dewasa, membuatnya cocok untuk setiap acara.
    </h2>
  </article>
  <article class="container">
    <h1 class="title">Kenapa Pilih </h1>
    <ul>
      <li>Pilihan Rasa yang Menggoda: Dari sosis sapi klasik hingga sosis pedas yang meriah, Mini Munchers menawarkan berbagai macam rasa lezat yang cocok untuk setiap selera. Ada sesuatu untuk dinikmati oleh semua orang!</li>
      <li>Porsi yang Sempurna: Mini Munchers kecil namun kaya rasa. Ukurannya yang kompak membuatnya ideal untuk dibagikan atau dinikmati sendiri, memastikan Anda bisa menikmati hotdog tanpa ada pemborosan.</li>
      <li>Kualitas yang Terpercaya: Di Mini Munchers, kami bangga menggunakan hanya bahan-bahan terbaik. Hotdog kami dibuat dengan daging berkualitas tinggi dan bahan-bahan terpilih, sehingga memberikan pengalaman camilan yang luar biasa setiap saat.</li>
    </ul>
  </article>
</main>
<footer class="bg-primary">
  <div class="footer-content">
    <h1 class="footer-title">Stalk us</h1>
    Instagram Youtube
  </div>
</footer>

<style>
  @media (max-width: 1440px) {
    .container {
      width: 100% !important;
    }
    .fg-banner{
      background-size: contain !important;
    }
    .navbar-brand{
      width: 86px !important;
      height: 86px !important;
    }
  }
  header {
    position: fixed;
    top: 0;
    width: 100vw;
    display: flex;
    flex-direction: column;
    align-items: center;
    transition: all 0.2s ease;
    background: none;
    z-index: 999;
  }
  nav {
    padding: 8px;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
  }
  .banner {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  footer {
    position: absolute;
    bottom: 0;
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  footer .container {
    display: flex;
    flex-direction: column;
    gap: 8px;
  }
  .banner .container, .banner-footer .container{
    width: 1440px;
    position: absolute;
    margin: auto;
  }
  .banner-footer .container{
    bottom: 0;
    height: 100%;
  }
  .container {
    width: 1440px;
  }
  .navbar-brand {
    width: 160px;
    height: 160px;
    box-shadow: none;
    transition: all 1s ease;
    border-radius: 100px;
  }
  .navbar-brand:hover {
    box-shadow: #ffbd02 1px 1px 16px;
  }
  .navbar-content {
    display: flex;
    flex-direction: row;
    gap: 16px;
  }
  .nav-link {
    text-decoration: none;
    color: white;
    background-color: rgba(100, 100, 100, 0.5);
    padding: 16px;
    font-size: large;
    transition: all 0.2s ease;
  }
  .nav-link:hover {
    background-color: #ffbd02;
    color: white !important;
  }
  .expand {
    box-shadow: #ffbd02 1px 1px 5px;
    background-color: #ffbd02;
  }
  .expand .nav-link {
    background-color: transparent;
    color: #55431c;
  }
  .expand .container .navbar-brand {
    width: 72px;
    height: 72px;
  }
  .banner {
    position: relative;
    width: 100%;
    /* height: 720px; */
    background-color: transparent;
    height: 100vh;
    overflow: hidden;
    /* z-index: -3; */
  }
  .banner-bg{
    height: 100%;
    width: 100%;
    background-color: #ffbd02;
    z-index: -99;
  }
  .circle-banner{
    z-index: -2;
    width: 80vw;
    height: 80vw;
    /* box-shadow: #55431c 1px 1px 100px; */
    border-radius: 50%;
    position: absolute;
    transform: translate(-50%, -50%);
    transition: top 0.3s ease, left 0.3s ease;
  }
  .fg-banner {
    background-color: transparent !important;
    bottom: 0px !important;
    right: 0px;
    position: absolute;
    width: 50% !important;
    height: 50% !important;
    transition: all 0.2s ease;
    z-index: -1;
  }
  .banner:hover .fg-banner {
    transform: scale(1.02);
  }
  /* .banner:hover .bg-banner{
    filter: blur(5px) grayscale(100%);
  } */
  .banner-title{
    position: absolute;
    top: calc(50% - 100px);
  }
  .banner-title h1{
    font-size: 96px;
    font-weight: 700;
  }
  .banner-footer {
    position: absolute;
    bottom: 0;
    display: flex;
    justify-content: center;
    height: 160px;
    width: 100%;
    background-color: white;
    z-index: 3 !important;
  }
  /* .banner-footer .container{
    position: relative;
    justify-content: flex-end;
    align-items: flex-end;
  } */
  .banner-footer .container a{
    position: absolute;
    bottom: calc(50% - 42px) !important;
  }
  .title {
    font-size: 120px;
  }
  .bg-primary {
    background-color: #ffbd02;
  }
  .footer-map {
    width: 100%;
    height: 320px;
    background-color: #aaa;
  }
  .content {
    margin-bottom: 420px;
  }
  .btn-lg{
    text-decoration: none;
    background-color: #55431c;
    color: #ffbd02;
    font-weight: 700;
    padding: 16px 16px;
    font-size: xx-large;
  }
</style>
