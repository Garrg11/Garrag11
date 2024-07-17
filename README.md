<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>التقاط صورة</title>
</head>
<body>
    <h1>التقاط صورة باستخدام الكاميرا</h1>
    <video id="video" width="640" height="480" autoplay></video>
    <button id="snap">التقاط صورة</button>
    <canvas id="canvas" width="640" height="480"></canvas>

    <script>
        // الحصول على عناصر الصفحة
        var video = document.getElementById('video');
        var canvas = document.getElementById('canvas');
        var context = canvas.getContext('2d');
        var snap = document.getElementById('snap');

        // الوصول إلى الكاميرا
        navigator.mediaDevices.getUserMedia({ video: true })
        .then(function(stream) {
            video.srcObject = stream;
            video.play();
        })
        .catch(function(err) {
            console.log("حدث خطأ: " + err);
        });

        // التقاط الصورة عند الضغط على الزر
        snap.addEventListener('click', function() {
            context.drawImage(video, 0, 0, 640, 480);
        });
    </script>
</body>
</html>
