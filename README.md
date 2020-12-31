# Livewire Dusk Testbench

---

## Overrides

```php
protected $packageProviders = [];
protected $withoutUI = false;
protected $storeConsoleLogs = false;
protected $captureFailures = false;
protected $appDebug = true;
protected $useDatabase = true;
protected $useFilesystemDisks = true;

public static $useSafari = false;

protected function getPackageProviders($app)
{
    return [
        ...parent::getPackageProviders($app),
        LivewireComponentsServiceProvider::class,
    ];
}

public function viewsDirectory()
{
    return __DIR__.'/views';
}

public function configureDatabase($app)
{
    $app['config']->set('database.default', 'testbench');
    $app['config']->set('database.connections.testbench', [
        'driver'   => 'sqlite',
        'database' => ':memory:',
        'prefix'   => '',
    ]);
}

public function configureFilesystemDisks($app)
{
    $app['config']->set('filesystems.disks.dusk-downloads', [
        'driver' => 'local',
        'root' => __DIR__.'/downloads',
    ]);
}

```

## App Key

Setup app key in phpunit file as per testbench instructions
