# re:Invent ALM Bootcamp Sample

![](https://s3.amazonaws.com/devops-bootcamp/img/alm-demo.png)

This is a sample PHP application for the re:Invent Application
Lifecycle Management bootcamp.

## Security

Add the following to httpd.conf:

    <Directory "/var/www/html/src">
        Order allow,deny
        Deny from all
    </Directory>

## Tests

    /usr/local/bin/phpunit --log-junit phpunit.xml src/SampleTest.php

## Installing PHPUnit on Jenkins

    sudo yum install php php-xml
    curl -Os https://phar.phpunit.de/phpunit.phar
    chmod +x phpunit.phar
    sudo mv phpunit.phar /usr/local/bin/phpunit

## Configuring Jenkins

In your project's configuration, click **Add Build Step** and then
**Shell**. Enter the following command:

    /usr/local/bin/phpunit --log-junit phpunit.xml src/SampleTest.php || true

![](https://s3.amazonaws.com/devops-bootcamp/img/build-01.png)

Click **Add Build Step** again. Select **Process xUnit test result
report**. Enter `0` for all of the threshold fields. Click **Add**,
and then choose **JUnit**. Next to **JUnit Pattern**, enter
`phpunit.xml`.

![](https://s3.amazonaws.com/devops-bootcamp/img/build-02.png)

Click **Save**.

#test
