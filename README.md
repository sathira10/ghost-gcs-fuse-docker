# ghost-gcs-fuse-docker
Ghost Docker image modified with support for Google Cloud Storage FUSE adapter (derived from the official community Ghost image)

Adds persistent storage to Ghost running on "Google Cloud Run" by means of a cloud storage bucket,
which is used as the "content" folder for the Ghost installation.

> The cloud storage bucket should be populated with the standard Ghost folders before running the app

## Environment variables
* $BUCKET (bucket-name)
* $MNT_DIR (content folder, defaults to "content")

## Deployment
A service account with storage permissions is needed to deploy the app. It can be deployed via gcloud as follows, 
or can be integrated with version control for continuous deployment.
```
gcloud beta run deploy filesystem-app --source . --execution-environment gen2 --allow-unauthenticated --service-account <service-account-name> --update-env-vars BUCKET=<bucket-name>
```

