# FTP Errors

> If a site had an update pushed to CloudCannon that is not appearing on the live site, it may be the FTP error.

Because of our IIS server setup, there may be issues when CloudCannon tries to FTP the new `_site/` build files.

CloudCannon uses a Linux-like environment when building a site. It also uses linux commands to do the FTP to external servers.

This is a section from a log file sent to us from CloudCannon from one of KCC's sites:
```
## CloudCannon `log.txt` file of the FTP log for one of KCC's sites

[16:54:57] > chmod: Access failed: 500 'SITE': command not understood (index)

[16:54:57] > chmod: Operation not supported: MFF and SITE CHMOD are not supported by this site

```

## The Error Screen

If a site had an update pushed to CloudCannon that is not appearing on the live site, it may be the FTP error. To check for the FTP error go into the CloudCannon interface. If the site you edited has a pulishing-workflow, go to the FTP version of the site (For Developer it would be named "Developer FTP" in CloudCannon).

