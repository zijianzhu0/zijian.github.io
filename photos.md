---
layout: default
title: Photos
---

# Photos

<section class="photo-gallery" aria-label="Photo gallery">
  <div class="photo-gallery__status">
    <p class="photo-gallery__count"><span id="photo-current">1</span> / <span id="photo-total">12</span></p>
  </div>

  <div class="photo-gallery__frame">
    <img
      class="photo-gallery__image"
      id="photo-image"
      src="{{ '/assets/photos/placeholder-01.svg' | relative_url }}"
      alt="Placeholder photo 01"
    />
  </div>

  <p class="photo-gallery__links">
    <a href="#" id="photo-prev">Prev</a>
    <span class="dot">·</span>
    <a href="#" id="photo-next">Next</a>
  </p>

  <p class="photo-gallery__caption" id="photo-caption">
    Placeholder caption 01. Replace this with a real caption when you add the final image.
  </p>
</section>

<script>
  (function () {
    var photos = [
      {
        src: {{ '/assets/photos/placeholder-01.svg' | relative_url | jsonify }},
        alt: "Placeholder photo 01",
        caption: "Placeholder caption 01. Replace this with a real caption when you add the final image."
      },
      {
        src: {{ '/assets/photos/placeholder-02.svg' | relative_url | jsonify }},
        alt: "Placeholder photo 02",
        caption: "Placeholder caption 02. A short note can sit here for context, mood, or where the photo was taken."
      },
      {
        src: {{ '/assets/photos/placeholder-03.svg' | relative_url | jsonify }},
        alt: "Placeholder photo 03",
        caption: "Placeholder caption 03. This space is reserved for the final caption text."
      },
      {
        src: {{ '/assets/photos/placeholder-04.svg' | relative_url | jsonify }},
        alt: "Placeholder photo 04",
        caption: "Placeholder caption 04. Use this line for a simple description or a longer reflection."
      },
      {
        src: {{ '/assets/photos/placeholder-05.svg' | relative_url | jsonify }},
        alt: "Placeholder photo 05",
        caption: "Placeholder caption 05. The caption updates as you move through the gallery."
      },
      {
        src: {{ '/assets/photos/placeholder-06.svg' | relative_url | jsonify }},
        alt: "Placeholder photo 06",
        caption: "Placeholder caption 06. Keep it short or expand it later when the real images are ready."
      },
      {
        src: {{ '/assets/photos/placeholder-07.svg' | relative_url | jsonify }},
        alt: "Placeholder photo 07",
        caption: "Placeholder caption 07. This follows the same one-image-at-a-time flow as the reference page."
      },
      {
        src: {{ '/assets/photos/placeholder-08.svg' | relative_url | jsonify }},
        alt: "Placeholder photo 08",
        caption: "Placeholder caption 08. You can later swap this with an actual photo title, place, or quote."
      },
      {
        src: {{ '/assets/photos/placeholder-09.svg' | relative_url | jsonify }},
        alt: "Placeholder photo 09",
        caption: "Placeholder caption 09. The navigation wraps, so next from the last image returns to the first."
      },
      {
        src: {{ '/assets/photos/placeholder-10.svg' | relative_url | jsonify }},
        alt: "Placeholder photo 10",
        caption: "Placeholder caption 10. Arrow keys also cycle through the photos."
      },
      {
        src: {{ '/assets/photos/placeholder-11.svg' | relative_url | jsonify }},
        alt: "Placeholder photo 11",
        caption: "Placeholder caption 11. This keeps the page easy to update without touching the layout."
      },
      {
        src: {{ '/assets/photos/placeholder-12.svg' | relative_url | jsonify }},
        alt: "Placeholder photo 12",
        caption: "Placeholder caption 12. Replace each placeholder block with your real image metadata later."
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
