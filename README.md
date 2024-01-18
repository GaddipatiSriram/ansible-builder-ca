# ansible-builder-ca

ansible-builder create --output-filename Dockerfile 
gsed -i 's/FROM/FROM --platform=linux\/amd64/' context/Dockerfile


ansible-builder build -v3 -t cloud-ee-base

docker tag cloud-ee-base:latest quay.io/sriramgaddipati/cloud-ee-base:latest

docker push quay.io/sriramgaddipati/cloud-ee-base:latest