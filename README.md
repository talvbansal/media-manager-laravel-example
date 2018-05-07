# Media-manager laravel example
This repository is a vanilla Laravel 5.5 install with the [media-manager](https://github.com/talvbansal/media-manager) package added to it.

After cloning it down you'll need to run the following commands to get it running:

```bash
composer install
cp .env.example .env
php artisan key:generate
php artisan storage:link
php artisan serve
```

Then simply navigate to [http://localhost:8000](http://localhost:8000) to see the media-manager running.
