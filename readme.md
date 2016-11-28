# Simple Cli CodeIgniter 3
A simple command line interface for the framework CodeIgniter 3.

### Features
- Create Controller
- Create Model
- Create Migration (*sequential or timestamp*)
- Run Migration

### Installation
**First**!
Download and copy the scli file to the project root developed with CodeIgniter 3.
Done! Simple, right?

### Creating Controller
```sh
$ php scli controller name_your_controller
```
or 
```sh
$ php scli c name_your_controller
```

### Creating Model
```sh
$ php scli model name_your_model
```
or 
```sh
$ php scli m name_your_model
```

### Creating Controller and Model
```sh
$ php scli cm name
```

### Creating Migration
Parameters:
- t: Set timestamp mode (*default*)
- s: Set sequential mode
- []: Table Attributes
```sh
$ php scli mi create_tbl_customers
```
or
```sh
$ php scli migration create_tbl_customers
```
result: *20161127161159_create_tbl_customers.php*
```sh
<?php
defined('BASEPATH') OR exit('No direct script access allowed');

class Migration_Create_tbl_customers extends CI_Migration {
   public function up()
   {
   }
   public function down()
   {
   }
}
```
Using **sequential** format and using **attributes**
```sh
$ php scli mi s create_tbl_customers [id,name,phone,address]
```
result: *001_create_tbl_customers.php*
```sh
<?php
defined('BASEPATH') OR exit('No direct script access allowed');

class Migration_Create_tbl_customers extends CI_Migration {
   public function up()
   {
        $this->dbforge->add_field(array(
            'id' => array(),
            'name' => array(),
            'phone' => array(),
            'address' => array()
        ));

        $this->dbforge->add_key('id', TRUE);
        $this->dbforge->create_table('YOUR_TABLE');
   }

   public function down()
   {
        $this->dbforge->drop_table('YOUR_TABLE', TRUE);
   }
}
```

### Running Migration
Run last migration
```sh
$ php scli migrate
```
or
```sh
$ php scli do:migrate
```

Run a specific version of the migration
```sh
$ php scli migrate value (sequential or timestamp)
```
or
```sh
$ php scli do:migrate value (sequential or timestamp)
```
### License


Licensed under the MIT License.
