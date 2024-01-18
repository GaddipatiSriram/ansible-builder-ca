# ansible-builder-ca

# create docker file and update the arch to amd64
ansible-builder create --output-filename Dockerfile 
gsed -i 's/FROM/FROM --platform=linux\/amd64/' context/Dockerfile

# build the image for amd64 using context/dockerfile
docker build --build-arg BUILDPLATFORM=linux/amd64,linux/arm64 -t cloud-ee-base:latest -f context/Dockerfile context/.

# tag the image and push to quay.io registry
docker tag cloud-ee-base:latest quay.io/sriramgaddipati/cloud-ee-base:latest
docker push quay.io/sriramgaddipati/cloud-ee-base:latest