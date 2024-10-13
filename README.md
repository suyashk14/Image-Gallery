<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Image Gallery</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
        }

        .gallery-container {
            max-width: 1000px;
            margin: 50px auto;
            padding: 20px;
            text-align: center;
        }

        .gallery-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
        }

        .gallery-item {
            width: 100%;
            height: auto;
            cursor: pointer;
            transition: transform 0.3s ease;
        }

        .gallery-item:hover {
            transform: scale(1.05);
        }

        .lightbox {
            display: none;
            position: fixed;
            z-index: 999;
            padding-top: 50px;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
        }

        .lightbox-content {
            margin: auto;
            display: block;
            width: 80%;
            max-width: 700px;
        }

        .prev, .next {
            cursor: pointer;
            position: absolute;
            top: 50%;
            width: auto;
            padding: 16px;
            color: white;
            font-weight: bold;
            font-size: 20px;
            transition: 0.3s ease;
            user-select: none;
        }

        .prev {
            left: 0;
        }

        .next {
            right: 0;
        }

        .prev:hover, .next:hover {
            background-color: rgba(0, 0, 0, 0.5);
        }

        .close {
            position: absolute;
            top: 20px;
            right: 35px;
            color: white;
            font-size: 40px;
            font-weight: bold;
            cursor: pointer;
            transition: 0.3s ease;
        }

        .close:hover {
            color: #ccc;
        }
    </style>
</head>
<body>
    <div class="gallery-container">
        <div class="gallery-grid">
            <img src="https://www.codealpha.tech/img/codealphalogo.png" alt="Image 1" class="gallery-item" onclick="openLightbox(0)">
            <img src="https://media.istockphoto.com/id/1382384282/photo/bangalore-or-bengaluru.jpg?s=1024x1024&w=is&k=20&c=knFJ__pEQhJ7QxtIXsG9Bd7_cgw5NtMxHxmoK0byA_k=" alt="Image 2" class="gallery-item" onclick="openLightbox(1)">
            <img src="https://media.istockphoto.com/id/2039582200/photo/woman-enjoying-sunset-over-the-sea-on-the-beach-near-her-car-travel-road-trip-and-tourism.jpg?s=1024x1024&w=is&k=20&c=lV5ccn9U5DzkwXmjKXkTmmLZJAw7j8WsuVwO_X16n0k=" alt="Image 3" class="gallery-item" onclick="openLightbox(2)">
            <img src="https://cdn.pixabay.com/photo/2023/10/15/11/38/street-8316703_1280.jpg" alt="Image 4" class="gallery-item" onclick="openLightbox(3)">
            
        </div>
    </div>

    <div id="lightbox" class="lightbox">
        <span class="close" onclick="closeLightbox()">&times;</span>
        <img id="lightbox-img" class="lightbox-content">
        <a class="prev" onclick="changeImage(-1)">&#10094;</a>
        <a class="next" onclick="changeImage(1)">&#10095;</a>
    </div>

    <script>
        let currentImageIndex = 0;
        const images = document.querySelectorAll('.gallery-item');
        const lightbox = document.getElementById('lightbox');
        const lightboxImg = document.getElementById('lightbox-img');

        function openLightbox(index) {
            currentImageIndex = index;
            lightbox.style.display = 'block';
            lightboxImg.src = images[currentImageIndex].src;
        }

        function closeLightbox() {
            lightbox.style.display = 'none';
        }

        function changeImage(step) {
            currentImageIndex = (currentImageIndex + step + images.length) % images.length;
            lightboxImg.src = images[currentImageIndex].src;
        }
    </script>
</body>
</html>
