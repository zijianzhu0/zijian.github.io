---
layout: default
title: Photos
---

# Photos

<section class="photo-gallery" aria-label="Photo gallery">
  <div class="photo-gallery__status">
    <p class="photo-gallery__count"><span id="photo-current">1</span> / <span id="photo-total">3</span></p>
  </div>

  <div class="photo-gallery__frame">
    <img
      class="photo-gallery__image"
      id="photo-image"
      src="{{ '/assets/photos/bike.jpeg' | relative_url }}"
      alt="Motorcyclist riding along a coastal road with one hand raised toward the cloudy sky."
    />
  </div>

  <p class="photo-gallery__links">
    <a href="#" id="photo-prev">Prev</a>
    <span class="dot">·</span>
    <a href="#" id="photo-next">Next</a>
  </p>

  <p class="photo-gallery__caption" id="photo-caption">
    A biker taking a selfie while riding a motorcycle.
  </p>
</section>

<script>
  (function () {
    var photos = [
      {
        src: {{ '/assets/photos/bike.jpeg' | relative_url | jsonify }},
        alt: "Motorcyclist riding along a coastal road with one hand raised toward the cloudy sky.",
        caption: "A biker taking a selfie while riding a motorcycle."
      },
      {
        src: {{ '/assets/photos/train station.jpeg' | relative_url | jsonify }},
        alt: "Commuters crossing a sunlit station concourse, blurred slightly in motion.",
        caption: "You either get busy living, or get busy dying."
      },
      {
        src: {{ '/assets/photos/crosswalk.jpeg' | relative_url | jsonify }},
        alt: "Woman offering a snack to a bundled-up child while standing at a city crosswalk.",
        caption: "Have you eaten?"
      }
    ];

    var image = document.getElementById("photo-image");
    var captionText = document.getElementById("photo-caption");
    var current = document.getElementById("photo-current");
    var total = document.getElementById("photo-total");
    var prev = document.getElementById("photo-prev");
    var next = document.getElementById("photo-next");
    var index = 0;

    function renderPhoto(nextIndex) {
      index = (nextIndex + photos.length) % photos.length;
      image.src = photos[index].src;
      image.alt = photos[index].alt;
      captionText.textContent = photos[index].caption;
      current.textContent = index + 1;
      total.textContent = photos.length;
    }

    prev.addEventListener("click", function (event) {
      event.preventDefault();
      renderPhoto(index - 1);
    });

    next.addEventListener("click", function (event) {
      event.preventDefault();
      renderPhoto(index + 1);
    });

    image.addEventListener("click", function () {
      renderPhoto(index + 1);
    });

    document.addEventListener("keydown", function (event) {
      if (event.key === "ArrowLeft") {
        renderPhoto(index - 1);
      }

      if (event.key === "ArrowRight") {
        renderPhoto(index + 1);
      }
    });

    renderPhoto(0);
  })();
</script>
