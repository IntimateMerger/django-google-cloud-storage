django-google-cloud-storage
===========================

Google Cloud Storage file backend for Django

If you run your projects on Google's appengine and you are using the django framework you might need this
file backend since there is no way to upload files, images, etc on appengine. Although solutions exist for
the amazon cloud storage i have not found a file backend for google cloud storage. This backend does work
with google cloud storage, although in early development. I have used it with regular file uploads and with
file manager solutions such as django-filer. The code as it is right now stores files for public use (i.e. a web site's images)

Prerequisites
-------------

You need to have an appengine project. This will not work as a standalone solution for non appengine django projects, since there is no authentication mechanism with the google cloud storage implemented.


### If you want to copy the files into your repository.

You need to install the GCS client library from
https://developers.google.com/appengine/docs/python/googlecloudstorageclient/download.

Just run `pip install GoogleAppEngineCloudStorageClient -t <your_app_directory/lib>`, or optionally, unzip the file and copy the `src/cloudstorage` folder into your project directory.

Installation
-------------

```
pip install git+https://github.com/IntimateMerger/django-google-cloud-storage.git@master
```

Or Just copy the google folder in your project directory

Configuration
-------------

On your django settings.py file you need to add the following settings

    GOOGLE_CLOUD_STORAGE_BUCKET = 'your_bucket_name'
    GOOGLE_CLOUD_STORAGE_URL = '//storage.googleapis.com/your_bucket_name/'
    GOOGLE_CLOUD_STORAGE_CACHE_CONTROL = 'public, max-age: 7200' # cache control headers

And finally declare the file storage backend you will use on your settings.py file

    DEFAULT_FILE_STORAGE = 'django_google_cloud_storage.GoogleCloudStorage'
