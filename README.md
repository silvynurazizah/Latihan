<p align="center">
 <img src="https://github.com/kmarsha/kasir-restoran/blob/master/public/img/welcome-page.png" alt="Project Welcome Page">
</p>
<h3 align="center">Our Café</h3>

<div align="center">

[![Repository](https://img.shields.io/badge/kmarsha-kasir--restoran-brown.svg)](https://github.com/kmarsha)
[![Status](https://img.shields.io/badge/status-closed-white.svg)]()

</div>

---

<p align="center"> Our Café is a cashier project based on a simple restaurant management
    <br> 
</p>

## 📝 Table of Contents

- [User Role](#user_role)
- [Flowchart](#flowchart)
- [Setting up a local environment](#getting_started)
- [Usage](#usage)
- [Preview](#preview)
- [Technology Stack](#tech_stack)
- [Authors](#authors)
- [Acknowledgments](#acknowledgments)

## 🧐 User Role <a name = "user_role"></a>

Completed with 4 Users
- Admin (managed Users)
- Cashier/Kasir (managed transactions)
- Manager/Manajer (managed menus and print transactions)
- Customer/Pelanggan (buy menu)

## 💡 Flowchart <a name = "flowchart"></a>

<p align="center"><img src="https://github.com/kmarsha/kasir-restoran/blob/master/public/img/flowchart.png"></p>

## 🏁 Getting Started <a name = "getting_started"></a>

These instructions will get you a copy of the project up and running on your local machine for development
and testing purposes. 

### Prerequisites

What things you need to install the software and how to install them.

```
PHP >= 8.0.12
```

### Installing

A step by step series of examples that tell you how to get a development env running.

Say what the step will be

```
git clone

composer install

composer update

cp .env.example .env

php artisan key:generate

CREATE DATABASE
```
modify .env file
```
php artisan migrate --seed

php artisan serve
```
open vendor\laravel\ui\auth-backend\AuthenticatesUsers.php 
  1) change public function username() to return 'username' not 'email'
  2) add sintaks below to protected function authenticated()
        ```
        if (Auth::user()->role == 'admin') {
            return redirect('/admin/registration');
        } elseif (Auth::user()->role == 'kasir') {
            return redirect('/kasir/transaction');
        } elseif (Auth::user()->role == 'manajer') {
            return redirect('/manajer/dashboard');
        }
        ```
  The Reason cause file under vendor not able to pushed

open app\Http\Kernel.php add sintaks below in last lined of protected $routeMiddleware array
        ```
        'admin' => \App\Http\Middleware\AdminMiddleware::class,
        'kasir' => \App\Http\Middleware\KasirMiddleware::class,
        'manajer' => \App\Http\Middleware\ManajerMiddleware::class,
        'customer' => \App\Http\Middleware\CustomerMiddleware::class,
        ```
  idk but kernel.php with config Middleware after clone is gone maybe cause composer install?

!! 🍭 Please notice that pdf print is not available just with php artisan serve / 127.0.0.1: but i use valet and it works 

## 🎈 Usage <a name="usage"></a>

Login with Role Admin
- Username = maccaa1
- Password = pass

Login with Role Kasir
- Username = maccaa2
- Password = pass

Login with Role Manajer
- Username = maccaa3
- Password = pass

Login with Role Pelanggan/Customer (may you prefer to register)
- Username = maccaa
- Password = pass

## 🌸 Preview <a name="preview"></a>
<img src="https://github.com/kmarsha/kasir-restoran/blob/master/public/img/page1.png">
<img src="https://github.com/kmarsha/kasir-restoran/blob/master/public/img/page2.png">
<img src="https://github.com/kmarsha/kasir-restoran/blob/master/public/img/page3.png">
<img src="https://github.com/kmarsha/kasir-restoran/blob/master/public/img/page4.png">
<img src="https://github.com/kmarsha/kasir-restoran/blob/master/public/img/page5.png">
<img src="https://github.com/kmarsha/kasir-restoran/blob/master/public/img/print1.png">
<img src="https://github.com/kmarsha/kasir-restoran/blob/master/public/img/print2.png">

## ⛏️ Built With <a name = "tech_stack"></a>

- [MySQL](https://www.mysql.com/) - Database
- [Laravel](https://laravel.com/) - Server Framework
- [Bootstrap](https://getbootstrap.com/) - Web Framework
- [NodeJs](https://nodejs.org/en/) - Server Environment
- [SweetAlert](https://sweetalert2.github.io/) - Notification

## ✍️ Authors <a name = "authors"></a>

- [@kmarsha](https://github.com/kmarsha) - Idea & Initial work
