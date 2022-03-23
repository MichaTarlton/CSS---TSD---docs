# TACL --help
Taken from the command for `TACL --help`

```shell
Usage: tacl [OPTIONS] [PNUM]

  tacl - TSD API client.

Options:
  --guide TEXT                  Print a guide
  --env TEXT                    API environment  [default: prod]
  --group TEXT                  Choose which file group should own the data
                                import

  --basic                       To use basic auth
  --upload TEXT                 Import a file or a directory located at given
                                path

  --upload-id TEXT              Identifies a specific resumable upload
  --resume-list                 List all resumable uploads
  --resume-delete TEXT          Delete a specific resumable upload
  --resume-delete-all           Delete all resumable uploads
  --download TEXT               Download a file
  --download-list               List files available for download
  --download-id TEXT            Identifies a download which can be resumed
  --version                     Show tacl version info
  --verbose                     Run tacl in verbose mode
  --config-show                 Show tacl config
  --config-delete               Delete tacl config
  --session-delete              Delete current tacl login session
  --register                    Register tacl for a specific TSD project and
                                API environment

  --ignore-prefixes TEXT        Comma separated list of sub folders to ignore
                                (based on prefix match)

  --ignore-suffixes TEXT        Comma separated list of files (based on suffix
                                match)

  --upload-cache-show           View the request cache
  --upload-cache-delete TEXT    Delete a request cache for a given key
  --upload-cache-delete-all     Delete the entire request cache
  --cache-disable               Disable caching for the operation
  --download-cache-show         View the request cache
  --download-cache-delete TEXT  Delete a request cache for a given key
  --download-cache-delete-all   Delete the entire request cache
  --upload-sync TEXT            Sync a local directory, incrementally
  --download-sync TEXT          Sync a remote directory, incrementally
  --cache-sync                  Enable caching for sync
  --keep-missing                Do not delete missing files in the target
                                directory while syncing

  --keep-updated                Do not over-write updated files in the target
                                directory while syncing

  --download-delete TEXT        Delete a file/folder which is available for
                                download

  --api-key TEXT                Pass an explicit API key - over-rides tacl
                                config

  --encrypt                     Use end-to-end encryption
  --chunk-size TEXT             E.g.: 10mb, size of chunks to both read from
                                disk, and send to the API

  --resumable-threshold TEXT    E.g.: 1gb, files larger than this size will be
                                sent as resumable uploads

  --help                        Show this message and exit.
```