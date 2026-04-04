---
layout: default
title: Photos
---

# Photos

<section class="photo-gallery" aria-label="Photo gallery">
  <p class="photo-gallery__locations">
    <a href="#tokyo" class="photo-location-link" data-photo-index="0" data-location="tokyo">tokyo</a>
    <span class="dot">·</span>
    <a href="#california" class="photo-location-link" data-photo-index="2" data-location="california">california</a>
    <span class="dot">·</span>
    <a href="#michigan" class="photo-location-link" data-photo-index="7" data-location="michigan">michigan</a>
    <span class="dot">·</span>
    <a href="#arizona" class="photo-location-link" data-photo-index="11" data-location="arizona">arizona</a>
  </p>

  <div class="photo-gallery__status">
    <p class="photo-gallery__count"><span id="photo-current">1</span> / <span id="photo-total">17</span></p>
  </div>

  <div class="photo-gallery__frame">
    <img
      class="photo-gallery__image"
      id="photo-image"
      src="{{ '/assets/photos/bike.jpeg' | relative_url }}"
      alt="A biker taking a selfie while riding a motorcycle, Kamakura."
    />
  </div>

  <p class="photo-gallery__links">
    <a href="#" id="photo-prev">Prev</a>
    <span class="dot">·</span>
    <a href="#" id="photo-next">Next</a>
  </p>

  <p class="photo-gallery__caption" id="photo-caption">
    A biker taking a selfie while riding a motorcycle, Kamakura.
  </p>
</section>

<script>
  (function () {
    var photos = [
      {
        src: {{ '/assets/photos/bike.jpeg' | relative_url | jsonify }},
        alt: "A biker taking a selfie while riding a motorcycle, Kamakura.",
        caption: "A biker taking a selfie while riding a motorcycle, Kamakura.",
        location: "tokyo"
      },
      {
        src: {{ '/assets/photos/train station.jpeg' | relative_url | jsonify }},
        alt: "You either get busy living, or get busy dying. Shinagawa station",
        caption: "You either get busy living, or get busy dying. Shinagawa station",
        location: "tokyo"
      },
      {
        src: {{ '/assets/photos/california-01.jpeg' | relative_url | jsonify }},
        alt: "San Francisco, a runner crossing the street with a historical building in the background.",
        caption: "San Francisco, a runner crossing the street with a historical building in the background.",
        location: "california"
      },
      {
        src: {{ '/assets/photos/california-02.jpg' | relative_url | jsonify }},
        alt: "Santa Monica, people riding spin bike on the beach.",
        caption: "Santa Monica, people riding spin bike on the beach.",
        location: "california"
      },
      {
        src: {{ '/assets/photos/california-03.jpg' | relative_url | jsonify }},
        alt: "A watertower, somewhere in SoCal.",
        caption: "A watertower, somewhere in SoCal.",
        location: "california"
      },
      {
        src: {{ '/assets/photos/california-04.jpg' | relative_url | jsonify }},
        alt: "Uptown Whitter, CA",
        caption: "Uptown Whitter, CA",
        location: "california"
      },
      {
        src: {{ '/assets/photos/california-05.jpg' | relative_url | jsonify }},
        alt: "Oceanside, CA",
        caption: "Oceanside, CA",
        location: "california"
      },
      {
        src: {{ '/assets/photos/michigan-01.jpeg' | relative_url | jsonify }},
        alt: "Sunny day after a snow storm, Michigan Tech",
        caption: "Sunny day after a snow storm, Michigan Tech",
        location: "michigan"
      },
      {
        src: {{ '/assets/photos/michigan-02.jpeg' | relative_url | jsonify }},
        alt: "During a snow storm, Michigan Tech",
        caption: "During a snow storm, Michigan Tech",
        location: "michigan"
      },
      {
        src: {{ '/assets/photos/michigan-03.jpeg' | relative_url | jsonify }},
        alt: "Skiing back in Michigan",
        caption: "Skiing back in Michigan",
        location: "michigan"
      },
      {
        src: {{ '/assets/photos/michigan-04.jpeg' | relative_url | jsonify }},
        alt: "Happy holidays sign at Michigan Tech",
        caption: "Happy holidays sign at Michigan Tech",
        location: "michigan"
      },
      {
        src: {{ '/assets/photos/arizona-01.jpeg' | relative_url | jsonify }},
        alt: "Sabino Canyon, Tucson",
        caption: "Sabino Canyon, Tucson",
        location: "arizona"
      },
      {
        src: {{ '/assets/photos/arizona-02.jpg' | relative_url | jsonify }},
        alt: "Mt. Lemmon Scenic Byway",
        caption: "Mt. Lemmon Scenic Byway",
        location: "arizona"
      },
      {
        src: {{ '/assets/photos/arizona-03.jpg' | relative_url | jsonify }},
        alt: "Tucson Downtown from Sentinel Peak.",
        caption: "Tucson Downtown from Sentinel Peak.",
        location: "arizona"
      },
      {
        src: {{ '/assets/photos/arizona-04.jpg' | relative_url | jsonify }},
        alt: "Gates Pass, Tucson",
        caption: "Gates Pass, Tucson",
        location: "arizona"
      },
      {
        src: {{ '/assets/photos/arizona-05.jpg' | relative_url | jsonify }},
        alt: "\"The Loop\" Trail, Tucson",
        caption: "\"The Loop\" Trail, Tucson",
        location: "arizona"
      },
      {
        src: {{ '/assets/photos/arizona-06.jpeg' | relative_url | jsonify }},
        alt: "Valencia Rd, Tucson",
        caption: "Valencia Rd, Tucson",
        location: "arizona"
      }
    ];

    var image = document.getElementById("photo-image");
    var captionText = document.getElementById("photo-caption");
    var current = document.getElementById("photo-current");
    var total = document.getElementById("photo-total");
    var prev = document.getElementById("photo-prev");
    var next = document.getElementById("photo-next");
    var locationLinks = document.querySelectorAll(".photo-location-link");
    var index = 0;

    function renderPhoto(nextIndex) {
      index = (nextIndex + photos.length) % photos.length;
      image.src = photos[index].src;
      image.alt = photos[index].alt;
      captionText.textContent = photos[index].caption;
      current.textContent = index + 1;
      total.textContent = photos.length;

      locationLinks.forEach(function (link) {
        link.classList.toggle("is-active", link.dataset.location === photos[index].location);
      });
    }

    prev.addEventListener("click", function (event) {
      event.preventDefault();
      renderPhoto(index - 1);
    });

    next.addEventListener("click", function (event) {
      event.preventDefault();
      renderPhoto(index + 1);
    });

    locationLinks.forEach(function (link) {
      link.addEventListener("click", function (event) {
        event.preventDefault();
        renderPhoto(Number(link.dataset.photoIndex));
      });
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
