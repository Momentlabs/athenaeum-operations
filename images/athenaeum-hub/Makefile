# Use google cloudbuild to create the image

GCP_PROJECT := momentlabs-jupyter
SHORT_SHA := "NO_SHA"
BRANCH := 'dev'
IMAGE := athenaeum-hub

default: 
	gcloud builds submit --substitutions BRANCH_NAME=${BRANCH},SHORT_SHA=${SHORT_SHA},_IMAGE=${IMAGE},_DOCKERFILE=. --config cloudbuild.yaml

# 	gcloud builds submit --tag gcr.io/$(GCP_PROJECT)/$(IMAGE):latest .

# gcr-staging:
# 	gcloud builds submit --tag gcr.io/$(GCP_PROJECT)/$(IMAGE):staging .

# gcr-production:
# 	gcloud builds submit --tag gcr.io/$(GCP_PROJECT)/$(IMAGE):production .


dh-build:
	docker build -t momentlabs/${IMAGE} .

dh-latest: dh-build
	docker push momentlabs/${IMAGE}

dh-dev: dh-build
	docker tag momentlabs/${IMAGE} momentlabs/${IMAGE}:56
	docker push momentlabs/${IMAGE}:56

dh-staging: dh-build
	docker tag momentlabs/${IMAGE} momentlabs/${IMAGE}:staging
	docker push momentlabs/${IMAGE}:staging

dh-production: dh-build
	docker tag momentlabs/${IMAGE} momentlabs/${IMAGE}:production
	docker push momentlabs/${IMAGE}:production
