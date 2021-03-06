# Italian petrol pumps comparator
![Italian petrol pumps comparator](http://fuel.reyboz.it/images/fuel-64px.png)

This web app allows you to list in a map and sort all fuel suppliers who are in a particular area, also it provides the current prices on every suppliers.

We have engineered this solution in a Hackathon that was sponsored by *Facile.it*, an Italian price comparator. This submission **won the competition**.

## Use
Use the http://fuel.reyboz.it online mirror. It has data updated on a daily basis.

## More about
Heroes and original technologies in the [/about.php](http://fuel.reyboz.it/about.php) page of the online mirror.

## Hacking
Go in your `www` folder and clone the source code using GNU Bazaar:

    bzr branch lp:it-fuel-stations-comparator

## Installation
Have GNU/Linux, PHP and MySQL/MariaDB working.

This project is built over the [Boz-PHP - Another PHP framework](https://github.com/valerio-bozzolan/boz-php-another-php-framework). Install it in your `/usr/share`:

    bzr branch lp:boz-php-another-php-framework /usr/share/boz-php-another-php-framework

Import in MySQL/MariaDB the `database-schema.sql` from the `installation` folder.

Also in the `installation` folder copy the `load-sample.php` in the root folder as `load.php` and fill with your MySQL/MariaDB credentials.

Remember to run the `cli/localize.sh` twice to enable translations.

Remember to install the `libjs-leaflet php-gettext` packages.

## Import data from MISE
Please download data from the Italian [Ministero dello Sviluppo Economico](http://www.sviluppoeconomico.gov.it/index.php/it/open-data/elenco-dataset/2032336-carburanti-prezzi-praticati-e-anagrafica-degli-impianti):
 * http://www.sviluppoeconomico.gov.it/images/exportCSV/prezzo_alle_8.csv
 * http://www.sviluppoeconomico.gov.it/images/exportCSV/anagrafica_impianti_attivi.csv

They are released under the terms of the Italian [Open Data License v2.0](http://www.dati.gov.it/iodl/2.0/).

### Manually import MISE .csv
The `cli/import-mise.php` helps you:

    php ./cli/import-mise.php anagrafica_impianti_attivi.csv prezzo_alle_8.csv

### Automatically download and import MISE .csv
Put a similar line in your cronjob:

    /var/www/cli/download-import-mise.sh "php /var/www/cli/import-mise.php"

.. or:

    su www-data -s /bin/sh -c '/var/www/cli/download-import-mise.sh "php /var/www/cli/import-mise.php"'

## Pull requests
Push in Launchpad:

https://code.launchpad.net/it-fuel-stations-comparator

## Translations
Translations are easily made using GNU Gettext. See the `l10n/` folder structure. Use something as Poedit to edit existing `.po` files or to create a new one from the `.pot`.

Remember to run the `cli/localize.sh` script before editing a `.po` file. Also run it *twice* when you finished.

The site language switcher is in the `load-post.php`. That part sucks but it works.

## License
This is a **Free** as in **Freedom** project. It comes with ABSOLUTELY NO WARRANTY. You are welcome to redistribute it under the terms of the **GNU Affero General Public License v3+**.
