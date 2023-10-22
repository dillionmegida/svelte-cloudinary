<script>
  import { CldImage, CldVideoPlayer } from "svelte-cloudinary"
  import { getContext } from "svelte"

  const products = getContext("products")
</script>

<main>
  <div class="container">
    <div class="single-image">
      <CldImage
        width={960}
        height={600}
        src="red-sneaker"
        alt="Color pair of sneakers"
      />
      <span class="single-image__unsplash">
        unsplash.com/photos/red-converse-all-star-high-top-sneaker-0BKZfcamvGg
      </span>
    </div>
    <div class="images_list">
      {#each products as product (product["public-id"])}
        <div class="images__item">
          <CldImage
            width={960}
            height={800}
            src={product["public-id"]}
            alt={product.alt}
            overlays={[
              {
                text: {
                  color: "rgb:ffffff",
                  fontFamily: "Poppins",
                  fontSize: 100,
                  fontWeight: "black",
                  text: "Brand",
                },
                effects: [{ opacity: 50 }],
              },
            ]}
          />

          <span class="images__item__unsplash">
            {product.unsplash}
          </span>
        </div>
      {/each}
    </div>

    <div class="video-section" />

    <CldVideoPlayer
      width="1620"
      height="1080"
      src="videos/demo-video"
      colors={{
        accent: "#000",
        base: "#fff000",
        text: "#ffffff",
      }}
      muted
      loop
      fontFace="Source Serif Pro"
    />
  </div>
</main>

<style>
  .single-image {
    /* background-color: #e3b5ff; */
  }

  .images_list {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 30px;
    margin-top: 50px;
  }
  .images__item, .single-image {
    box-shadow: 1px 1px 10px color-mix(in srgb, black, transparent 90%);
  }

  .images__item__unsplash, .single-image__unsplash {
    font-size: 10px;
    display: block;
    padding: 10px 20px;
  }

  .video-section {
    margin-top: 50px;
  }
</style>
