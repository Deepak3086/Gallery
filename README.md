# Ex.08 Design of Interactive Image Gallery
# Date:18/11/2024
# AIM:
To design a web application for an inteactive image gallery with minimum five images.

# DESIGN STEPS:
## Step 1:
Clone the github repository and create Django admin interface.

## Step 2:
Change settings.py file to allow request from all hosts.

## Step 3:
Use CSS for positioning and styling.

## Step 4:
Write JavaScript program for implementing interactivity.

## Step 5:
Validate the HTML and CSS code.

## Step 6:
Publish the website in the given URL.

# PROGRAM :

gallery.html
~~~

<html>
    <head>
  <title>Interactive Image Gallery</title>
  <link rel="stylesheet" href="gallery.css">
</head>
<body>
  <h1>Interactive Image Gallery</h1>
  <div class="gallery">
    <div class="slides">
      <div class="frame">
        <div class="image-container">
          <img src="pictures/taj_mahal.jpg" alt="India" />
          <div class="caption">Taj mahal</div>
        </div>
        <div class="image-container">
          <img src="pictures/spain.jpg" alt="Spain" />
          <div class="caption">Sagrada Familia</div>
        </div>
        <div class="image-container">
          <img src="pictures/thailand.jpg" alt="Thailand" />
          <div class="caption">Maya Bay</div>
        </div>
        <div class="image-container">
          <img src="pictures/victoria.jpg" alt="Zambia" />
          <div class="caption">Victoria falls</div>
        </div>
      </div>
    </div>
      
    <div class="slides">
      <div class="frame">
        <div class="image-container">
          <img src="pictures/italy.jpg" alt="Italy" />
          <div class="caption">Manorola</div>
        </div>
        <div class="image-container">
            <img src="pictures/france.jpg" alt="France" />
            <div class="caption"> Arc de Triomphe</div>
        </div>
        <div class="image-container">
            <img src="pictures/china.jpg" alt="China" />
            <div class="caption">Seiganto-ji Temple</div>
        </div>
        <div class="pictures/brazil.jpg">
            <img src="pictures/brazil.jpg" alt="Brazil" />
            <div class="caption">Christ The Redeemer</div>
        </div>
      </div>
    </div> 

    <div class="slides">
      <div class="frame">
        <div class="image-container">
          <img src="pictures/bali.jpg" alt="Bali" />
          <div class="caption">Ulun Danu Beratan Temple</div>
        </div>
        <div class="image-container">
          <img src="pictures/africa.jpg" alt="Africa" />
          <div class="caption">Serengeti</div>
        </div>
      </div>
    </div>
    <a class="prev" onclick="plusSlides(-1)">&#10094;</a>
    <a class="next" onclick="plusSlides(1)">&#10095;</a>

    <div class="dot-class">
      <span class="dot" onclick="currentSlide(1)"></span>
      <span class="dot" onclick="currentSlide(2)"></span>
      <span class="dot" onclick="currentSlide(3)"></span>
    </div>
      <script src="gallery.js"></script>
    </body>
</html>
~~~

gallery.css
~~~
body {
    font-family: Arial, sans-serif;
    text-align: center;
    margin: 0;
    padding: 0;
  }
  
  h1 {
    margin: 20px 0;
  }
  
  .gallery {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 20px;
    padding: 20px;
  }
  
  .image-container {
    position: relative;
    width: 40%;
    height: 100%;
    overflow: hidden;
    border: 2px solid #ddd;
    transition: transform 0.3s;
  }
  .frame{
    width: 100%;
    height: 70vh;
    display: flex;
    justify-content: center;
    gap: 20px;
  }
  
  .image-container:hover {
    cursor: pointer;
    transform: scale(1.1);
    border-color: #333;
  }
  
  .image-container img {
    width: 100%;
    height: 100%;
    object-fit:cover;
  }
  
  .caption {
    position: absolute;
    bottom: 0;
    background: rgba(0, 0, 0, 0.6);
    color: #fff;
    width: 100%;
    padding: 5px;
    text-align: center;
    font-size: 14px;
    visibility: hidden;
    transition: visibility 0.3s;
  }
  
  .image-container:hover .caption {
    visibility: visible;
  }
  
  
  .prev, .next {
    cursor: pointer;
    position: absolute;
    top: 50%;
    width: auto;
    margin-top: -22px;
    padding: 16px;
    color: white;
    font-weight: bold;
    font-size: 18px;
    background-color: rgba(0,0,0,0.8);
    transition: 0.6s ease;
    border-radius: 0 3px 3px 0;
    user-select: none;
  }
  .slides{
    width: 80%;
    height: 100%;
  }
  
  .prev{
    left: 0;
    border-radius: 3px 0 0 3px;
    margin-left: 120px;
  }
  .next {
    right: 0;
    border-radius: 0  3px 3px 0;
    margin-right: 120px;
  }
  
  .prev:hover, .next:hover {
    transform: scale(1.2);
  }
  
  .dot {
    cursor: pointer;
    height: 15px;
    width: 15px;
    margin: 0 2px;
    background-color: #bbb;
    border-radius: 50%;
    display: inline-block;
    transition: background-color 0.6s ease;
  }
  .dot-class{
    position: absolute;  
    bottom: 20px;        
    left: 50%;           
    transform: translateX(-50%); 
    display: flex;       
    gap: 5px;            
    z-index: 10; 
  }
  .active, .dot:hover {
    background-color: #717171;
  }
  ~~~

  gallery.js
  ~~~
  document.querySelectorAll('.image-container').forEach(container => {
    container.addEventListener('click', () => {
      alert('You clicked on ' + container.querySelector('.caption').textContent);
    });
  });
  let slideIndex = 1;
  showSlides(slideIndex);
  
  // Next/previous controls
  function plusSlides(n) {
    showSlides(slideIndex += n);
  }
  
  // Thumbnail image controls
  function currentSlide(n) {
    showSlides(slideIndex = n);
  }
  
  function showSlides(n) {
    let i;
    let slides = document.querySelectorAll(".slides");
    let dots = document.getElementsByClassName("dot");
    if (n > slides.length) {slideIndex = 1}
    if (n < 1) {slideIndex = slides.length}
    for (i = 0; i < slides.length; i++) {
      slides[i].style.display = "none";
    }
    for (i = 0; i < dots.length; i++) {
      dots[i].className = dots[i].className.replace(" active", "");
    }
    slides[slideIndex-1].style.display="block";
    dots[slideIndex-1].className += " active";
  }
   function openModal(imageSrc, imageAlt) {
    let modal = document.getElementById('imageModal');
    if (!modal) {
      modal = document.createElement('div');
      modal.id = 'imageModal';
      modal.style.cssText = `
        display: flex; 
        position: fixed; 
        top: 0; 
        left: 0; 
        width: 100%; 
        height: 100%; 
        background-color: rgba(0, 0, 0, 0.8); 
        justify-content: center; 
        align-items: center;
        z-index: 1000;
      `;
  
      const modalImg = document.createElement('img');
      modalImg.id = 'modalImg';
      modalImg.style.cssText = `
        max-width: 90%; 
        max-height: 90%; 
        box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.6);
      `;
  
      const closeModal = document.createElement('span');
      closeModal.innerHTML = '&times;';
      closeModal.style.cssText = `
        position: absolute; 
        top: 20px; 
        right: 30px; 
        color: white; 
        font-size: 40px; 
        font-weight: bold; 
        cursor: pointer;
      `;
      closeModal.addEventListener('click', () => {
        modal.style.display = 'none';
      });
  
      modal.appendChild(modalImg);
      modal.appendChild(closeModal);
      document.body.appendChild(modal);
    }
  
    const modalImg = document.getElementById('modalImg');
    modalImg.src = imageSrc;
    modalImg.alt = imageAlt;
    modal.style.display = 'flex';
  }

  ~~~
# OUTPUT:
![alt text](<Screenshot 2024-12-14 190738.png>)
![alt text](<Screenshot 2024-12-18 101422.png>)

![alt text](<Screenshot 2024-12-14 190817.png>)
![alt text](<Screenshot 2024-12-14 190836.png>)
# RESULT:
The program for designing an interactive image gallery using HTML, CSS and JavaScript is executed successfully.
