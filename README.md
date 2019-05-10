# laravel_notification

Sample laravel notification to email and database

Steps:

1. Config your database and email in .env file. You can use log for mail driver for testing sending mail

2. Create notification file
    ```
    php artisan make:notification SubscriptionRenewalFailed
    ```

3. Create notification table for notification database
    ```
    php artisan notification:table
    ```

4. Install laravel scope to check the email
    ```
    composer require laravel/telescope --dev
    ```

5. Update routes\web.php
    ```
    use App\Notifications\SubscriptionRenewalFailed;

    Route::get('/', function () {
        $user = App\User::first();

        $user->notify(new SubscriptionRenewalFailed);
        
        return 'Done';
    });
    ```

6. Run the app and open it in the browser. After the page load, you can check the email in the telescope mail 
   tab and notification data in the telescope queries tab


