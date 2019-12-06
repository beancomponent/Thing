# How to Upgrade
1. Remove vendor folder as well as composer.lock file
1. `composer update`
1. Copy require-dev from symfony skeleton to package's composer.json's require-dev
1. `composer require symfony/property-access --dev`
1. `composer require dama/doctrine-test-bundle --dev`
1. `composer req orm --dev`
1. `composer req test --dev`

# How to prepare for Dev
1. composer install
1. Open .env.test.local paste these lines into it
    -  `DATABASE_URL="sqlite:///%kernel.project_dir%/var/app.db"`
1. Change the *src* folder name in services.yaml to *src-symfony*
1. Copy the following snippet to doctrine.yaml under *mappings* configuration
```
            Bean\Tests\Thing:
                 is_bundle: false
                 type: annotation
                 dir: '%kernel.project_dir%/tests/Doctrine/Orm'
                 prefix: 'Bean\Tests\Thing\Doctrine\Orm'
                 alias: App
```
 
# Dev Workflow
1. Make change to code
2. `php bin/phpunit`