# Build image support run flask web server
docker build . -f Dockerfile -t mywebflask

# Push to docker hub
docker push mywebflask

# Run container base on mywebflask image
docker run mywebflask