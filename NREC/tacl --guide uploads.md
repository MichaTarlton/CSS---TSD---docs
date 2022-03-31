# tacl --guide uploads
taken from the command `tacl --guide uploads`

```shell
tacl --guide uploads

Upload a single file:

    tacl p11 --upload myfile.txt

Files larger than 1GB are resumable if something goes wrong:

    tacl p11 --upload myfile.txt --upload-id 52928fed-8c29-4135-88e9-27f2c0bec526

To browse and manage resumables:

    tacl p11 --resume-list
    tacl p11 --resume-delete 52928fed-8c29-4135-88e9-27f2c0bec526
    tacl p11 --resume-delete-all

Uploading directories (automatically resumable for the whole directory):

    tacl p11 --upload mydirectory

To control which folders and files are included:

    tacl p11 --upload mydirectory --ignore-prefixes .git,build,dist --ignore-suffixes .pyc,.db

To disable the resume functionality for a directory:

    tacl p11 --upload mydirectory --cache-disable

To view and manage directory upload cache:

    tacl p11 --upload-cache-show
    tacl p11 --upload-cache-delete mydirectory
    tacl p11 --upload-cache-delete-all

Using on-the-fly encryption, with automatic server-side decryption:

 tacl p11 --upload myfile.txt --encrypt
 tacl p11 --upload mydirectory --encrypt

```