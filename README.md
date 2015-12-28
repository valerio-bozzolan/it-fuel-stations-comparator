# Italian petrol pumps comparator
![Italian petrol pumps comparator](http://fuel.reyboz.it/images/fuel-64px.png)

This web app allows you to list in a map and sort all fuel suppliers in a particular area, also it provides the current prices of every suppliers.

We have engineered this solution durring a Hackathon sponsored by *Facile.it*, an Italian price comparison website. Our submission **won the competition**.

## Use
Use the http://fuel.reyboz.it online mirror. Its data is updated on a daily basis.

## More about
The original heroes and used technologies can be found in the [/about.php](http://fuel.reyboz.it/about.php) page of the online mirror.

## Hacking
Go in your `www` folder and clone the source code using Bazaar:

    bzr branch lp:it-fuel-stations-comparator

## Installation
Have GNU/Linux, PHP and MySQL/MariaDB working.

This project is built over the [Boz-PHP - Another PHP framework](https://github.com/valerio-bozzolan/boz-php-another-php-framework). Install it in your `/usr/share`:

    bzr branch lp:boz-php-another-php-framework /usr/share/boz-php-another-php-framework

Import in MySQL/MariaDB the `database-schema.sql` from the `installation` folder.

Also in the `installation` folder copy the `load-sample.php` in the root folder as `load.php` and fill with your MySQL/MariaDB credentials.

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

## License
This is a **Free** as in **Freedom** project. It comes with ABSOLUTELY NO WARRANTY. You are welcome to redistribute it under the terms of the **GNU Affero General Public License v3+**.
