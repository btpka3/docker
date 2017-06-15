



## prepare custom fonts

```bash
############################################# for MacOS users
mkdir -p ~/my-fonts
cp "/System/Library/Fonts/PingFang.ttc"                 ~/my-fonts

cp "/System/Library/Fonts/Hiragino Sans GB W3.ttc"      ~/my-fonts
cp "/System/Library/Fonts/Hiragino Sans GB W6.ttc"      ~/my-fonts
cp "/System/Library/Fonts/STHeiti Light.ttc"            ~/my-fonts
cp "/System/Library/Fonts/STHeiti Medium.ttc"           ~/my-fonts
cp "/Library/Fonts/Songti.ttc"                          ~/my-fonts

locate Kaiti.ttc
cp "/System/Library/Assets/com_apple_MobileAsset_Font3/f349bda554d1242dc7f20742e6f738d587d7139a.asset/AssetData/Kaiti.ttc"  \
                                                        ~/my-fonts
                                                        
# TransType : dfont -> ttf
#cp "/System/Library/Fonts/HelveticaNeue.dfont"          ~/my-fonts
#cp "/System/Library/Fonts/Helvetica.dfont ~/my-fonts"   ~/my-fonts

############################################# for Ubuntu users
# after manual install `ttf-mscorefonts-installer` :
scp -r root@yourUbuntuHost:/usr/share/fonts/truetype/msttcorefonts ~/my-fonts
```

## run

```bash
#docker stop my-c2 && docker rm my-c2
docker run \
    --name my-c2 \
    -p 9222:9222 \
    -v ~/my-fonts:/usr/share/fonts/my-fonts \
    -i \
    -t \
    -d \
    btpka3/chrome-headless:0.1.0

# manual update font cache
docker exec -u root my-c2 bash -c '
cd /usr/share/fonts/my-fonts
#mkfontscale
#mkfontdir
fc-cache -fv
fc-list | sort
'
```

## reference
* [Getting Started with Headless Chrome](https://developers.google.com/web/updates/2017/04/headless-chrome)
* [Chrome DevTools Protocol](https://chromedevtools.github.io/devtools-protocol/)
* [chrome-remote-interface](https://github.com/cyrus-and/chrome-remote-interface)
* [justinribeiro/chrome-headless](https://hub.docker.com/r/justinribeiro/chrome-headless/)
* [btpka3/my-chrome-eggjs](https://github.com/btpka3/btpka3.github.com/tree/master/js/chrome/my-chrome-eggjs)
* [TransType](https://www.fontlab.com/font-converter/transtype/)
* [dfontsplitter](https://peter.upfold.org.uk/projects/dfontsplitter)
