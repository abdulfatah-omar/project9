# project9
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Image Slider Exercise</title>
  <link rel="stylesheet" href="./style.css">
</head>
<body>
  <h1>Image Slider</h1>

  <!-- Write your HTML here -->  <div class="container">
    <div class="project-heading">
      <h1 class="title">Image Slider</h1>
      <div class="subtitle">Click the buttons to change the image!</div>
    </div>

    <div id="slider">
      <img src="https://picsum.photos/id/1005/500/400" alt="Image 1">
      <img src="https://picsum.photos/id/1012/500/400" alt="Image 2">
      <img src="https://picsum.photos/id/1015/500/400" alt="Image 3">
      <img src="https://picsum.photos/id/1024/500/400" alt="Image 4">
      <button id="prev">&lt;</button>
      <button id="next">&gt;</button>
    </div>
  </div>


  <script src="./script.js"></script>
</body>
</html>


@import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');


*, *::before, *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}


body {
  font-family: "Poppins", sans-serif;
  background-color: #f0f0f0;
  color: #333;
  transition: all 0.4s ease-in;
}


h1 {
  text-align: center;
  margin-top: 1.25rem;
}


.container {
  display: grid;
  width: 100%;
  min-height: calc(100vh - 4.25rem);
  place-content: center;
  gap: 1rem;
  text-align: center;
}


/* Write your CSS below */


#slider {
  position: relative;
  width: 500px;
  height: 400px;
}


#slider img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  opacity: 0;
  transition: all 1s ease-in-out;
}
#slider img.active {
  opacity: 1;
}
button {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  border: 3px solid #fff;
  border-radius: 50%;
  width: 70px;
  height: 70px;
  background-color: #717171;
  color: #f1f1f1;
  font-size: 32px;
  font-stretch: condensed;
  cursor: pointer;
  transition: all 200ms ease-in-out;
}
button:hover {
  background-color: steelblue;
}
button#prev {
  left: -35px;
  padding: 7px 17px 7px 15px;
}

button#next {
  right: -35px;
  padding: 7px 15px 7px 17px;
}
const images = document.querySelectorAll('#slider img');
const previousImage = document.getElementById("prev");
const nextImage = document.getElementById("next");

let currentIndex = 0;

function reset() {
  for (let i = 0; i < images.length; i++) {
    images[i].classList.remove('active');
  }
}

function initializeSlider() {
  reset();
  images[currentIndex].classList.add('active');
}

function slideLeft() {
  reset();
  currentIndex--;
  if (currentIndex < 0) {
    currentIndex = images.length - 1;
  }
  images[currentIndex].classList.add('active');
}

function slideRight() {
  reset();
  currentIndex++;
  if (currentIndex >= images.length) {
    currentIndex = 0;
  }
  images[currentIndex].classList.add('active');
}

initializeSlider();

previousImage.addEventListener('click', function() {
  slideLeft();
});

nextImage.addEventListener('click', function() {
  slideRight();
});




























