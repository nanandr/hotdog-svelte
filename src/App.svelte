<script>
  import {onMount} from 'svelte'
  import logo from './assets/logo.png'
  import banner from './assets/banner.jpg'
  import fgBanner from './assets/fg-banner.png'

  let scrollY = 0
  let expandNavbar = ''
  onMount(() => {
    window.addEventListener('scroll', handleScroll)
    return () => {
      window.removeEventListener('scroll', handleScroll)
    }
  })
  function handleScroll(){
    scrollY = window.scrollY
  }
  $: {
    expandNavbar = scrollY > 600 ? 'expand' : ''
  }
</script>

<main>
  <header class="{expandNavbar}">
    <nav class="container">
      <div class="navbar-brand" style="background-image: url({logo});"></div>
      <div class="navbar-content">
        <a href="#" class="nav-link">Product</a>
        <a href="#" class="nav-link">#</a>
        <a href="#" class="nav-link">#</a>
      </div>
    </nav>
  </header>
  <div class="banner">
    <div class="bg-banner" style="background-image: url({banner});">
    </div>
    <div class="fg-banner container" style="background-image: url({fgBanner});">
    </div>
    <section class="container">
      <h1 class="banner-title">Hotdog Enak</h1>
    </section>
  </div>
  <section class="content container">
    <h1 class="title">Lorem ipsum dolor, sit amet</h1>
    <p>
      Lorem ipsum dolor sit amet, consectetur adipisicing elit. Vero iste possimus dolor non necessitatibus assumenda perspiciatis odio maiores magni aspernatur. Quaerat, rem atque! Facilis natus nisi porro totam dolorem unde.
      Lorem, ipsum dolor sit amet consectetur adipisicing elit. Asperiores harum nisi minima est odit alias eius soluta, tempora facilis vero eaque earum neque dolorum pariatur! Expedita quam illum qui vel!
    </p>
  </section>
  <footer class="bg-primary">
    <div class="footer-map">
      google map
    </div>
    <div class="container">
      <div class="footer-content">
        <h1 class="footer-title">
          Stalk us
        </h1>
        Instagram
        Youtube
      </div>
    </div>
  </footer>
</main>

<style>
  @media(max-width: 1440px){
    .container{
      width: 100% !important;
    }
    /* .banner{
      height: 420px !important;
    } */
  }
  header{
    position: fixed;
    top: 0;
    width: 100vw;
    display: flex;
    flex-direction: column;
    align-items: center;
    transition: all 0.2s ease;
    background: none;
    z-index: 1;
  }
  nav{
    padding: 8px;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
  }
  main, .banner{
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  main{
    position: relative;
    justify-content: flex-start;
    min-height: 2560px;
  }
  footer{
    position: absolute;
    bottom: 0;
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  footer .container{
    display: flex;
    flex-direction: column;
    gap: 8px;
  }
  .container{
    width: 1440px;
  }
  .navbar-brand{
    width: 160px;
    height: 160px;
    box-shadow: none;
    transition: all 1s ease;
    border-radius: 100px;
  }
  .navbar-brand:hover{
    box-shadow: #FFBD02 1px 1px 16px;
  }
  .navbar-content{
    display: flex;
    flex-direction: row;
    gap: 16px;
  }
  .nav-link{
    text-decoration: none;
    color: white;
    background-color: rgba(100, 100, 100, 0.5);
    padding: 16px;
    font-size: large;
    transition: all 0.2s ease;
  }
  .nav-link:hover{
    background-color: #FFBD02;
    color: white !important;
  }
  .expand{
    box-shadow: #aaa 1px 1px 5px;
    background-color: #FFBD02;
  }
  .expand .nav-link{
    background-color: transparent;
    color: #55431C;
  }
  .expand .container .navbar-brand{
    width: 72px;
    height: 72px;
  }
  .banner{
    position: relative;
    width: 100%;
    /* height: 720px; */
    height: 100vh;
  }
  .fg-banner, .bg-banner{
    position: absolute;
    top: 0;
    width: 100%;
    height: 100%;
  }
  .bg-banner{
    filter: blur(10px);
    transition: all 1s ease;
  }
  .fg-banner{
    transition: all 0.2s ease;
  }
  .banner:hover .fg-banner{
    transform: scale(1.02);
  }
  /* .banner:hover .bg-banner{
    filter: blur(5px) grayscale(100%);
  } */
  .banner .container{
    position: absolute;
    bottom: 16px;
  }
  .banner-title{
    font-size: 120px;
    color: white;
  }
  .title{
    font-size: 120px;
  }
  .bg-primary{
    background-color: #FFBD02;
  }
  .footer-map{
    width: 100%;
    height: 320px;
    background-color: #aaa;
  }
  .content{
    margin-bottom: 420px;
  }
</style>
