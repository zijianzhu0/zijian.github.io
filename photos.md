---
layout: default
title: Photos
---

# Photos

<section class="photo-gallery" aria-label="Photo gallery">
  <p class="photo-gallery__locations">
    <a href="#tokyo" id="tokyo" class="photo-location-link" data-photo-index="0" data-location="tokyo">tokyo</a>
    <span class="dot">·</span>
    <a href="#yuzawa" id="yuzawa" class="photo-location-link" data-photo-index="5" data-location="yuzawa">yuzawa</a>
    <span class="dot">·</span>
    <a href="#california" id="california" class="photo-location-link" data-photo-index="6" data-location="california">california</a>
    <span class="dot">·</span>
    <a href="#michigan" id="michigan" class="photo-location-link" data-photo-index="11" data-location="michigan">michigan</a>
    <span class="dot">·</span>
    <a href="#arizona" id="arizona" class="photo-location-link" data-photo-index="15" data-location="arizona">arizona</a>
    <span class="dot">·</span>
    <a href="#alaska" id="alaska" class="photo-location-link" data-photo-index="21" data-location="alaska">alaska</a>
  </p>

  <div class="photo-gallery__status">
    <p class="photo-gallery__count"><span id="photo-current">1</span> / <span id="photo-total">23</span></p>
  </div>

  <button class="photo-gallery__frame" id="photo-image-next" type="button" aria-label="Show next photo">
    <img
      class="photo-gallery__image"
      id="photo-image"
      src="{{ '/assets/photos/bike.jpeg' | relative_url }}"
      alt="A biker taking a selfie while riding a motorcycle, Kamakura."
    />
  </button>

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
    var gallery = document.querySelector(".photo-gallery");
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
        src: {{ '/assets/photos/tokyo-chill.jpg' | relative_url | jsonify }},
        alt: "A person relaxing on the grass in a Tokyo park.",
        caption: "Taking it easy in a Tokyo park.",
        location: "tokyo"
      },
      {
        src: {{ '/assets/photos/tokyo-from-above.jpg' | relative_url | jsonify }},
        alt: "A visitor looking over Tokyo from a high-rise observation deck.",
        caption: "Tokyo from above.",
        location: "tokyo"
      },
      {
        src: {{ '/assets/photos/tokyo-tiffany.jpg' | relative_url | jsonify }},
        alt: "A person sitting beside bicycles outside a Tiffany & Co. storefront in Tokyo.",
        caption: "Outside Tiffany & Co., Tokyo.",
        location: "tokyo"
      },
      {
        src: {{ '/assets/photos/yuzawa.jpeg' | relative_url | jsonify }},
        alt: "Four snowboarders riding a chairlift above snowy mountains in Yuzawa.",
        caption: "Chairlift in Yuzawa.",
        location: "yuzawa"
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
        alt: "Uptown Whittier, CA",
        caption: "Uptown Whittier, CA",
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
      },
      {
        src: {{ '/assets/photos/alaska-pier.jpg' | relative_url | jsonify }},
        alt: "A marina filled with boats beneath snow-streaked mountains in Alaska.",
        caption: "A marina beneath the mountains, Alaska.",
        location: "alaska"
      },
      {
        src: {{ '/assets/photos/alaska-speed-limit.jpg' | relative_url | jsonify }},
        alt: "A speed limit 65 sign beside water and snow-covered mountains in Alaska.",
        caption: "Speed limit 65, Alaska.",
        location: "alaska"
      }
    ];

    var image = document.getElementById("photo-image");
    var imageNext = document.getElementById("photo-image-next");
    var captionText = document.getElementById("photo-caption");
    var current = document.getElementById("photo-current");
    var total = document.getElementById("photo-total");
    var prev = document.getElementById("photo-prev");
    var next = document.getElementById("photo-next");
    var locationLinks = document.querySelectorAll(".photo-location-link");
    var index = 0;

    function indexFromHash() {
      var location = window.location.hash.slice(1);
      var link = document.querySelector('.photo-location-link[data-location="' + location + '"]');
      return link ? Number(link.dataset.photoIndex) : 0;
    }

    function renderPhoto(nextIndex, syncHash, alignGallery) {
      index = (nextIndex + photos.length) % photos.length;
      image.src = photos[index].src;
      image.alt = photos[index].alt;
      captionText.textContent = photos[index].caption;
      current.textContent = index + 1;
      total.textContent = photos.length;

      locationLinks.forEach(function (link) {
        var isActive = link.dataset.location === photos[index].location;
        link.classList.toggle("is-active", isActive);
        if (isActive) {
          link.setAttribute("aria-current", "true");
        } else {
          link.removeAttribute("aria-current");
        }
      });

      if (syncHash && window.location.hash !== "#" + photos[index].location) {
        history.replaceState(null, "", "#" + photos[index].location);
      }

      if (alignGallery) {
        requestAnimationFrame(function () {
          gallery.scrollIntoView({ block: "start" });
        });
      }
    }

    prev.addEventListener("click", function (event) {
      event.preventDefault();
      renderPhoto(index - 1, true, true);
    });

    next.addEventListener("click", function (event) {
      event.preventDefault();
      renderPhoto(index + 1, true, true);
    });

    locationLinks.forEach(function (link) {
      link.addEventListener("click", function (event) {
        renderPhoto(Number(link.dataset.photoIndex), false, true);
      });
    });

    imageNext.addEventListener("click", function () {
      renderPhoto(index + 1, true, true);
    });

    document.addEventListener("keydown", function (event) {
      var target = event.target;
      if (event.defaultPrevented || event.altKey || event.ctrlKey || event.metaKey || event.shiftKey ||
          target.matches("a, button, input, select, textarea") || target.isContentEditable) {
        return;
      }

      if (event.key === "ArrowLeft") {
        renderPhoto(index - 1, true, true);
      }

      if (event.key === "ArrowRight") {
        renderPhoto(index + 1, true, true);
      }
    });

    window.addEventListener("hashchange", function () {
      renderPhoto(indexFromHash(), false, true);
    });

    renderPhoto(indexFromHash(), false, false);
  })();
</script>
