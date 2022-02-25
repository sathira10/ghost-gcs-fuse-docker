# ghost-gcs-fuse-docker
Ghost Docker image modified with support for Google Cloud Storage FUSE adapter (derived from the official community Ghost image)

This image was created to add persistent storage to Ghost running on "Google Cloud Run" by means of a cloud storage bucket. 
It uses a cluod stoarge bucket as the "content" folder for the Ghost installation.

> The cloud storage bucket should be populated with the standard Ghost folders running the app

## Environment variables
* $BUCKET (bucket-name)
* $MNT_DIR (content folder, defaults to "content")

## Deployment
A service account with neccessary permissions should be used to deploy the app. It can be deployed via local machine as follows, 
or can be integrated with version control for continuous deployment.
```
gcloud beta run deploy filesystem-app --source . --execution-environment gen2 --allow-unauthenticated --service-account <service-account-name> --update-env-vars BUCKET=<bucket-name>
```

