Atitit video 播放器使用总结

  <!-- video js-->
  <link href="https://vjs.zencdn.net/7.4.1/video-js.css" rel="stylesheet">
  <script src='https://vjs.zencdn.net/7.4.1/video.js'></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/videojs-contrib-hls/5.15.0/videojs-contrib-hls.min.js"></script>

  <!--  
  <link href="../app_videomd/video-js.css" rel="stylesheet">
  <script src='../app_videomd/video.js'></script>
  <script src="../app_videomd/videojs-contrib-hls.min.js"></script>
  -->
  <style>
    .player-dimensions {
      width: 100%;
    }
  </style>
  <!-- video js end-->




   <div class="video">
        <video id="player" class="video-js vjs-styles-defaults">

            

             <script type="text/javascript">
        
              get_sync("/vod/vod_list_byid.php?vid="+getQueryVar('vid'),(dt)=>{
                     arr=   JSON.parse(dt);
                     o=arr[0];
                    
                    //  url=o.vod_pwd_url.split("$")[1];
                      url=o.vod_play_url.split("$")[1];
                      console.log(url)

                     vdsrc=`  <source   src="${url}">`
                    document.writeln(vdsrc);
                     
      
              })
            </script>

        </video>
        <div id="playList"></div>
      </div>

Js
 <script >

        var player = videojs('player', {
          controls: true, //控制条：boolean
          controlBar: {
            playToggle: {
              replay: true
            },
            progressControl: true
          }
        }, function onPlayerReady() {
          // 修改this指向
          var vdthis = this;
          videojs.log('播放器已经准备好了!');
    
          //this.play();
    
          this.on('ended', function () {
            videojs.log('播放结束了!');
          });
        });
      </script>


读取动态url

  必须使用同步js ajax获取，否则初始化不了。。。
