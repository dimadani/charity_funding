<script>
  import { onMount, onDestroy, beforeUpdate, afterUpdate } from 'svelte';
  import Header from '../components/Header.svelte';
  import Footer from '../components/Footer.svelte';
  import { charities } from '../data/charities.js';

  export let params; 
  let data;
  
  function getCharity(id) {
    return charities.find(function (charity) {
      return charity.id === parseInt(id);
    })
  };
  
  // data = getCharity(params.id);
  
  onMount(function() {
    setTimeout(() => {
      data = getCharity(params.id);
    },1000);
  })

  beforeUpdate(() => {
    console.log('dieksekusi sebelum dom berhasil di update');
  })

  afterUpdate(() => {
    console.log('dieksekusi setelah dom berhasil di update');
  })

  let interval = setInterval(() => {
    second += 1,
    console.log(second);
  },1000);
  
  onDestroy(() =>{
    clearInterval(interval)
    console.log('dieksekusi setelah component ini dihancurkan');
  });
</script>

<style>
  #xs-input-checkbox {
    display: flex;
    align-items: center;
  }
  #xs-donate-agree {
    width: 30px;
  }
  label[for="xs-donate-agree"] {
    margin: 0;
    margin-left: 11px;
  }
</style>

<Header />
<!-- welcome section -->
<!--breadcumb start here-->
{#if data}
<section class="xs-banner-inner-section parallax-window"
  style="background-image:url('https://images.unsplash.com/photo-1532629345422-7515f3d16bb6?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=3000&q=80 3000whttps://images.unsplash.com/photo-1532629345422-7515f3d16bb6?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1950&q=80 1950w')">
  <div class="xs-black-overlay"></div>
  <div class="container">
    <div class="color-white xs-inner-banner-content">
      <h2>Donate Now</h2>
      <p>{data.title}</p>
      <ul class="xs-breadcumb">
        <li class="badge badge-pill badge-primary">
          <a href="/" class="color-white">Home /</a> Donate
        </li>
      </ul>
    </div>
  </div>
</section>
<!--breadcumb end here-->
<!-- End welcome section -->
<main class="xs-main">
  <!-- donation form section -->
  <section class="xs-section-padding bg-gray">
    <div class="container">
      <div class="row">
        <div class="col-lg-6">
          <div class="xs-donation-form-images"><img
              src="{data.thumbnail}"
              class="img-responsive" alt="Family Images"></div>
        </div>
        <div class="col-lg-6">
          <div class="xs-donation-form-wraper">
            <div class="xs-heading xs-mb-30">
              <h2 class="xs-title">{data.title}</h2>
              <p class="small">To learn more about make donate charity
                with us visit our "<span class="color-green">Contact
                  us</span>" site. By calling <span class="color-green">+44(0) 800 883 8450</span>.</p><span
                class="xs-separetor v2"></span>
            </div><!-- .xs-heading end -->
            <form action="#" method="post" id="xs-donation-form" class="xs-donation-form" name="xs-donation-form">
              <div class="xs-input-group">
                <label for="xs-donate-name">Donation Amount <span class="color-light-red">**</span></label> <input
                  type="text" name="name" id="xs-donate-name" class="form-control" placeholder="Minimum of $5">
              </div><!-- .xs-input-group END -->
              <div class="xs-input-group">
                <label for="xs-donate-charity">List of Evaluated Charities
                  <span class="color-light-red">**</span></label>
                <select name="charity-name" id="xs-donate-charity" class="form-control">
                  <option value="">
                    Select
                  </option>
                  <option value="amarokSocity">
                    Amarok socity
                  </option>
                  <option value="amarokSocity">
                    Amarok socity
                  </option>
                </select>
              </div><!-- .xs-input-group END -->
              <div class="xs-input-group" id="xs-input-checkbox">
                <input type="checkbox" name="agree" id="xs-donate-agree" />
                <label for="xs-donate-agree">
                  I Agree
                  <span class="color-light-red">**</span>
                </label>
              </div>
              <button type="submit" class="btn btn-warning"><span class="badge"><i class="fa fa-heart"></i></span>
                Donate
                now</button>
            </form><!-- .xs-donation-form #xs-donation-form END -->
          </div>
        </div>
      </div><!-- .row end -->
    </div><!-- .container end -->
  </section><!-- End donation form section -->
</main>
{/if}
<Footer />