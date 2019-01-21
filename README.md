# ansible deployment for managing music with mpd
deploys: mpd, ympd as web frontend and a self written music downloader (music comes from deezer)  

The deezer downloader can be found here: https://gitlab.com/kmille/deezer-downloader

Tested with Debian Stretch. For simple testing use `vagrant up` which automatically uses ansible.

Required variables are:
- music_dir: < dir mpd looks for>
- deezer_email: < deezer username (free subscription)>
- deezer_password: < deezer password >
- deezer_download_dir: < dir for deezer downloads (must be with within music_dir)

music_dir and deezer_download_dir without trailing slashes please.


# Screenshot
![Alt text](https://image.ibb.co/cjBC30/screen.png "KISS")

run it with: ansible-playbook music.yaml --ask-sudo-pass  
(ajdust your ssh config to get password less ssh access. then will ask for a password)  

if you have to ajdust the routes in the front end (e.g downloader is not under / but /deezer)
sed -i 's@/static/@/deezer/static/@' app/templates/index.html  
sed -i 's@/api/@/deezer/api/@' app/static/js/custom.js  
maybe you have to restart gunicorn  
 

