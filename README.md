### Cronjob-capable shell script to download backups from Mantis bugtracker

This script:
- automatically logs in to Mantis, see section "Configuration" in the
  script.
- tells Mantis to create a fresh backup.
- checks whether the date of the backup as reported by Mantis matches
  the local time to ensure backup creation worked.
- downloads the backup into a directory called YYYY-MM-DD, or fails
  if it already exists.
- tests the CRCs of the zip files of the backup.
- sets the timestamps of the zip files to that of the newest contained
  file.
- aborts with non-zero exit code and prints an error if any of the above
  fails. If your have a working ```mail``` command available on your
  system cron daemons such as ```anachron``` will typically mail this
  output to you.
- prints nothing upon success to ensure you don't get unnecessary emails
  from cron.

**Notice**: As of 2018 it seems the feature to create a backup on the
web interface is only available on MantisHub, not in stock Mantis.
Hence this script likely only will work with MantisHub.

### Dependencies

```shell
apt-get install bash wget grep unzip
```