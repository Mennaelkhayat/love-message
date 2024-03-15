<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>I Love You</title>
    <style>
        body, html {
            height: 100%;
            margin: 0;
            padding: 0;
            background-color: #F4C2C2; /* Baby pink */
            overflow: hidden;
        }
        .center-message {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 48px; /* Larger font size */
            font-weight: bold; /* Bolder font */
            color: white;
            z-index: 2; /* Ensure text is above the hearts */
        }
        .heart {
            position: absolute;
            animation: float 5s linear infinite;
            color: #ff69b4; /* Brighter heart color for better visibility */
            z-index: 1;
        }
        @keyframes float {
            0% {
                transform: translateY(100vh) scale(0.5);
                opacity: 1;
            }
            100% {
                transform: translateY(-100vh) scale(1.5); /* End larger and off the screen */
                opacity: 0;
            }
        }
        /* Adjustments for smaller screens */
        @media (max-width: 600px) {
            .center-message {
                font-size: 32px; /* Smaller font for small devices */
            }
        }
        /* Reduce animations for users who prefer reduced motion */
        @media (prefers-reduced-motion: reduce) {
            .heart {
                animation: none;
            }
        }
    </style>
</head>
<body>

<div class="center-message">I Love You</div>

<script>
    function randomBetween(min, max) {
        return Math.floor(Math.random() * (max - min + 1) + min);
    }

    function createHeart() {
        const heart = document.createElement('div');
        heart.classList.add('heart');
        heart.innerHTML = '❤️';
        heart.style.fontSize = `${randomBetween(24, 48)}px`; // Bigger hearts
        heart.style.left = `${randomBetween(0, 100)}vw`;
        heart.style.animationDuration = `${randomBetween(3, 8)}s`; // Randomize animation speed
        document.body.appendChild(heart);

        setTimeout(() => {
            heart.remove();
        }, 8000); // Longer than the longest animation duration to ensure it's not removed too early
    }

    setInterval(createHeart, 300);
</script>
</body>
</html>
