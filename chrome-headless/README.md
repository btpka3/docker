
docker rm my-c

docker run \
    --name my-c \
    -i \
    -t \
    -d \
    btpka3/chrome-headless:0.1.0 \
    google-chrome-stable \
    --headless \
    --disable-gpu \
    --no-sandbox \
    --remote-debugging-address=0.0.0.0 \
    --remote-debugging-port=9222


docker stop my-c1
docker rm my-c1
docker run \
    --name my-c1 \
    -p 9222:9222 \
    -i \
    -t \
    -d \
    my-c-img  
    
docker exec -it my-c1 bash