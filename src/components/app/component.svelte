<div ref:carousel class="glide">
  <div class="glide__arrows" data-glide-el="controls">
    <div class="glide__arrow glide__arrow--left" data-glide-dir="<">
      LEFT
    </div>
    <div class="glide__arrow glide__arrow--right" data-glide-dir=">">
      RIGHT
    </div>
  </div>
  <div class="glide__track" data-glide-el="track">
    <ul class="glide__slides">
      {#each images as image}
      <li class="glide__slide">
      </li>
      {/each}
    </ul>
  </div>
  <div class="glide__bullets" data-glide-el="controls[nav]">
    {#each images as image, i}
      <button class="glide__bullet" data-glide-dir="={i}"></button>
    {/each}
  </div>
</div>

<style>
  .glide__arrow {
    border: none;
    padding: 0;
    box-shadow: none;
  }

  .glide__slide {
    height: 260px;
    background-size: cover;
    background-position: 50%;
  }
</style>

<script>
  import Glide, { Controls, Breakpoints, Autoplay } from '@glidejs/glide/dist/glide.modular.esm'

  export default {
    data () {
      return {
				images: []
      }
    },

    oncreate () {
      const { carousel } = this.refs
      const glide = new Glide(carousel, {
        type: 'carousel',
        perView: 1
      })

      this.set({ glide })
      
      glide.mount({
        Controls,
        Breakpoints,
        Autoplay
      })
    },

    ondestroy () {
      const { glide } = this.get()
      glide.destroy()
    }
  }
</script>