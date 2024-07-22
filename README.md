<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="css/style.css">
    <script src="https://kit.fontawesome.com/4628f4cb20.js" crossorigin="anonymous"></script>
</head>
<body>
    <div class="container">
        <div class="Music-Player">
            <nav>
                <div class="circle">
                    <i class="fa-solid fa-angle-left"></i>

                </div>
                <div class="circle">
                    <i class="fa-solid fa-bars"></i>
                </div>
            </nav>
            <img src="css/singer_pic.jpg" class="song-img">
            <h2>Hua Hain Aaj Pehli Baar </h2>
            <p>Arman-Malik</p>

           <audio controls id="song">
            <source src="css/myFav.mp3" type="audio/mpeg">
           </audio>

           <input type="range" value="0"id="progress">
           <div class="controls">
            <div><i class="fa-solid fa-backward"></i></div>
            <div onclick="playPause()"><i class="fa-solid fa-play" id="ctrlIcon"></i></div>
            <div><i class="fa-solid fa-forward"></i></div>
           </div>

        </div>

    </div>

    <script>

        let progress=document.getElementById("progress");
        let song=document.getElementById("song");
        let ctrlIcon=document.getElementById("ctrlIcon");
        

        song.onloadedmetadata=function(){
            progress.max=song.durataion;
            progress.value=song.currentTime;

        }

        function playPause(){
            if(ctrlIcon.classList.contains("fa-pause")){
                song.pause();
                ctrlIcon.classList.remove("fa-pause");
                ctrlIcon.classList.add("fa-play");
            }
            else{
                song.play();
                ctrlIcon.classList.add("fa-pause");
                ctrlIcon.classList.remove("fa-play");
            }
        }


        if(song.play()){
            setInterval(()=>{
                progress.value=song.currentTime;
            },500);
        }
        progress.onchange=function(){
            song.play();
            song.currentTime=progress.value;
            ctrlIcon.classList.add("fa-pause");
            ctrlIcon.classList.remove("fa-play");
        }
    </script>
    
    
</body>
</html>
