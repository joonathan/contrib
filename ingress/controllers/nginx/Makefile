all: push

# 0.0 shouldn't clobber any release builds
TAG = 0.5
PREFIX = gcr.io/google_containers/nginx-ingress-controller

controller: controller.go clean
	CGO_ENABLED=0 GOOS=linux godep go build -a -installsuffix cgo -ldflags '-w' -o nginx-ingress-controller

container: controller
	docker build -t $(PREFIX):$(TAG) .

push: container
	gcloud docker push $(PREFIX):$(TAG)

clean:
	rm -f nginx-ingress-controller
