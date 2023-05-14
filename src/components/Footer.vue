<template>
  <footer class="footer">
    <div class="container">
      <div class="footer-content">
        <img src="../assets/icons/footer/logo.svg" alt="logo">
        <div class="footer-wrapper">
          <h4 class="footer-title">Platform</h4>
          <ul class="footer-list">
            <li class="footer-item"><a href="#">Overview</a></li>
            <li class="footer-item"><a href="#">Features</a></li>
            <li class="footer-item"><a href="#">About</a></li>
            <li class="footer-item"><a href="#">Pricing</a></li>
          </ul>
        </div>
        <div class="footer-wrapper">
          <h4 class="footer-title">Help</h4>
          <ul class="footer-list">
            <li class="footer-item"><a href="#">How does it work?</a></li>
            <li class="footer-item"><a href="#">Where to ask questions?</a></li>
            <li class="footer-item"><a href="#">How to pay?</a></li>
            <li class="footer-item"><a href="#">What is needed for this?</a></li>
          </ul>
        </div>
        <div class="footer-wrapper">
          <h4 class="footer-title">Contacts</h4>
          <ul class="footer-list">
            <li class="footer-item"><a href="tel:9967165323577">(716) 532-3577</a></li>
            <li class="footer-item">116 Archer Rd <br> Broadalbin, New York(NY), 12025</li>
          </ul>
        </div>
      </div>
      <div class="footer-bottom">
        <p class="footer-description">2022 - 2023. Единая зачетная книжка</p>
        <ul class="footer-cocial-list">
          <li class="footer-cocial-item"><a href="#" target="_blank"><img src="../assets/icons/footer/facebook.svg"
                alt="cocial-icon"></a></li>
          <li class="footer-cocial-item"><a href="#" target="_blank"><img src="../assets/icons/footer/twiter.svg"
                alt="cocial-icon"></a></li>
          <li class="footer-cocial-item"><a href="#" target="_blank"><img src="../assets/icons/footer/instagram.svg"
                alt="cocial-icon"></a></li>
          <li class="footer-cocial-item"><a href="#" target="_blank"><img src="../assets/icons/footer/in.svg"
                alt="cocial-icon"></a></li>
        </ul>
      </div>
    </div>
  </footer>
</template>

<script setup>
import FooterIcon from '../assets/icons/footer/FooterIcon.vue';

</script>

<style lang="scss">
.footer {
  &-title {
    font-weight: 500;
    font-size: 16.2px;
    line-height: 140%;
    color: #000000;
    margin-bottom: 25px;
    
  }

  &-list {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  &-item {
    font-weight: 400;
    font-size: 14.4px;
    line-height: 140%;
    letter-spacing: 0.05em;
    color: rgba(1, 8, 81, 0.8);  
  }

  &-content {
    display: flex;
    align-items: start;
    justify-content: space-between;
    padding: 50px 0 100px;
    border-bottom: 1px solid #010851;
  }

  &-bottom {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 66px 0 80px;
  }

  &-cocial-list {
    display: flex;
    align-items: center;
    gap: 50px;
  }
}
@media screen and (max-width:930px) {
  .footer {
    &-content {
      flex-wrap: wrap;
      gap: 60px;
      justify-content: left;
    }
    &-bottom {
      padding: 20px 0;
    }
  }
}
@media screen and (max-width:610px) {
  .footer {
    &-content {
      border-bottom: unset;
          flex-direction: column;
    /* justify-content: center; */
    align-items: center;
    text-align: center;
    }
     
    &-bottom {
      padding: 20px 0; 
      flex-direction: column-reverse;
      text-align: center;
    }
  }
}
@media screen and (max-width:533px) {
  .footer { 
      
  }
}
</style>