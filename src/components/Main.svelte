<script>
  import { onMount } from "svelte";
  import { navigate } from "svelte-routing";
  let canvas;
  let ctx;

  onMount(() => {
    ctx = canvas.getContext("2d")
    new Animation(canvas, ctx)
  })

  class Animation {
    constructor(canvas, ctx) {
      this.canvas = canvas;
      this.ctx = ctx;
      this.stageWidth = document.body.clientWidth;
      this.stageHeight = document.body.clientHeight;
      this.A = [0, this.stageHeight]
      this.B = [this.stageWidth, this.stageHeight]
      this.canvas.width = this.stageWidth;
      this.canvas.height = this.stageHeight;
      requestAnimationFrame(this.animate.bind(this));
    }
    update(t) {
      this.A[1] -= Math.cos(t / 1000) * Math.PI;
      this.B[1] -= Math.sin(t / 1000) * Math.PI;
    };
    draw(ctx) {
      ctx.beginPath();
      ctx.fillStyle = "rgb(0, 122, 255)";
      ctx.moveTo(...this.A);
      ctx.lineTo(0, this.stageHeight);
      ctx.lineTo(this.stageWidth, this.stageHeight);
      ctx.lineTo(...this.B);
      ctx.lineTo(...this.A);
      ctx.fill();
    };

    animate (t) {
      ctx.clearRect(0, 0, this.stageWidth, this.stageHeight);
      this.update(t);
      this.draw(this.ctx);
      requestAnimationFrame(this.animate.bind(this));
    };
  }
</script>
<style lang="scss">
  @import "../scss/_definition.scss";
  .container {
    width: 100%;
    min-height: 100%;
    @include custom-flex(center, center, column);
    p {
      font-size: 96px;
      font-weight: 900;
    }
    button {
      margin-top: 72px;
      color: white;
      font-size: 24px;
      padding: 12px 72px;
      transition: transform 0.5s;
      background-color: $sub-main-color;
      &:hover {
        transform: scale(1.03);
      }
    }
    .main {
      color: $main-color;
    }
    .sub-main {
      color: $sub-main-color;
    }
    canvas {
      position: fixed;
      z-index: -1;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      pointer-events: none;
    }
  }
</style>

<div class="container">
  <p>Welcome to <span class="main">T</span>ravel-<span class="sub-main">I</span>nfo</p>
  <button on:click={() => {navigate("/map")}}>Let's start</button>
  <button on:click={()=>{navigate("/list")}}>
    리스트</button>
  <canvas bind:this={canvas}></canvas>
</div>
