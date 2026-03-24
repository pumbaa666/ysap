Pumbaa's Home Page
============

HTML version : https://pumbaa.ch
Bash version : `curl https://pumbaa.ch`

Forked from https://github.com/bahamas10/ysap

Usage
-----

```bash
make help
make build         # default target, builds the site into ./_site
make check-deps    # check to ensure needed dependencies are installed
make check         # check tools syntax using shellcheck
make serve         # serve site locally out of ./_site
make deploy        # deploy the site (using scp)
make all           # build and deploy the site
make clean         # remove any generated files (./_site/*)
```

Apache2 config
-----
```text
<VirtualHost *:443>
    ServerName pumbaa.ch
    DocumentRoot /var/www/html

    RewriteEngine On

    # Serves custom bash page when the user curl or wget root of pumbaa.ch
    RewriteCond %{HTTP_USER_AGENT} (curl|wget) [NC]
    RewriteRule ^/$ /index.bash [L]
</VirtualHost>
```