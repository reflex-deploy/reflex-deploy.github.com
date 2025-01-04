<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mouse Reveal Wallpaper</title>
    <style>
        body {
            margin: 0;
            overflow: hidden;
            height: 100vh;
            cursor: none;
        }

        .container {
            position: relative;
            width: 100%;
            height: 100%;
        }

        .wallpaper {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: url('https://via.placeholder.com/1920x1080') no-repeat center center/cover;
            filter: brightness(0);
            transition: filter 0.2s ease;
        }

        .cursor {
            position: absolute;
            width: 150px;
            height: 150px;
            background: rgba(255, 255, 255, 0.5);
            border-radius: 50%;
            pointer-events: none;
            mix-blend-mode: lighten;
            transform: translate(-50%, -50%);
        }

    </style>
</head>
<body>
    <div class="container">
        <div class="wallpaper"></div>
        <div class="cursor"></div>
    </div>

    <script>
        const cursor = document.querySelector('.cursor');
        const wallpaper = document.querySelector('.wallpaper');

        document.addEventListener('mousemove', (e) => {
            const x = e.clientX;
            const y = e.clientY;

            // Move the cursor element
            cursor.style.left = `${x}px`;
            cursor.style.top = `${y}px`;

            // Reveal the wallpaper where the cursor is
            wallpaper.style.filter = `brightness(100%)`;
        });

        document.addEventListener('mouseleave', () => {
            cursor.style.opacity = `0`;
            wallpaper.style.filter = `brightness(0)`;
        });

        document.addEventListener('mouseenter', () => {
            cursor.style.opacity = `1`;
        });
    </script>
</body>
</html>
