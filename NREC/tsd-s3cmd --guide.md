# tsd-s3cmd --guide
Taken from the command `tsd-s3cmd --guide`
```
tsd-s3cmd  
~~~~~~~~~  
  
Usage: tsd-s3cmd [OPTIONS]  
  
Using the s3 API  
~~~~~~~~~~~~~~~~  
  
   1. Create a .s3cfg in your HOME directory.  
  
   Your TSD project's access and secret key can be found in:  
   /tsd/pXX/data/durable/s3-api-access-keys. The config file  
   should look like this:  
  
       host_base = api.tsd.usit.no  
       host_bucket = api.tsd.usit.no  
       # include the following bucket_location line even though it is not used  
       bucket_location = us-east-1  
       use_https = True  
       access_key = ACCESS_KEY  
       secret_key = SECRET_KEY  
       signature_v2 = False  
  
   2. Now register your tsd-s3cmd with your TSD project:  
  
       tsd-s3cmd --register  
       # choose 'prod'  
  
   This will prompt you for your TSD credentials. To register for p11, for example,  
   enter your p11 credentials. Similar for any other projects. You have to  
   register for each project you have access to. The above command stores an API  
   key in a config file in your HOME directory. API keys are projects specific,  
   and allow you to authenticate. By themselves they do not give access to TSD.  
  
   3. Create a bucket (e.g. named mybucket):  
  
       tsd-s3cmd mb s3://mybucket  
  
   4. Upload data:  
  
   To upload a single file  
  
       tsd-s3cmd put file s3://mybucket  
  
   If the upload fails for some reason, tsd-s3cmd will print an id, which you can use  
   to resume the upload as follows:  
  
       tsd-s3cmd --upload-id id put file s3://mybucket  
  
   You can also specify explicit chunk sizes  
  
       tsd-s3cmd --multipart-chunk-size-mb=200 put data s3://mybucket  
  
   You can also synchronise directories this is useful if your directory  
   changes in incremental ways and you only want to transfer the diff to TSD  
  
       tsd-s3cmd --multipart-chunk-size-mb=200 sync dir s3://mybucket  
  
   Restart the sync if it fails  
  
       tsd-s3cmd --multipart-chunk-size-mb=200 --upload-id id sync dir s3://mybucket  
  
   5. Download data  
  
   Data can only be exported from the 'export-bucket'. This is a folder in TSD,  
   located at /tsd/pXX/data/durable/s3-api/export-bucket. This folder is only  
   accessible by member of the pXX-export-group.  
  
   Then outside TSD:  
  
       tsd-s3cmd ls s3://export-bucket  
       tsd-s3cmd get s3://export-bucket/myfile  
  
   6. To interact with the test API:  
  
       tsd-s3cmd --usetest [OPTIONS]  
  
      To interactive with the alt/fx03 API:  
  
       tsd-s3cmd --usealt [OPTIONS]  
  
   7. If you have a long-lasting upload which requires batch programming  
   You can request an import token, save it, and use s3cmd directly. For  
   guidance on how to do this, do e.g.:  
  
       tsd-s3cmd --print-token-for put  
  
   8. For more help and examples of s3cmd client usage:  
  
       tsd-s3cmd --s3cmd-help  
  
   Or browse http://s3tools.org/s3cmd
```