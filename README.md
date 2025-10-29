# DevOps Multi-API Project

A complete full-stack application demonstrating API development with Laravel, Go, and React frontend.

## 🏗️ Project Structure

```
devops/
├── laravel/          # Laravel API (PHP)
├── go/              # Go API 
├── frontend/        # React.js Frontend
├── compare_apis.sh  # API comparison script
└── README.md        # This file
```

## How to Install Apps
Git install
```bash
apt update
apt install git
git --version
```

mysql install
```bash
apt install mysql-server
mysql_secure_installation
systemctl status mysql
```

create database
```bash
mysql
create database if not exists laravel;
show databases;
create user 'dian’@’localhost' identified by 'Q@eqwe123';
grant all privileges on *.* to ‘dian’@’localhost’;
SELECT user, host FROM mysql.user;
flush privileges;
exit;
```

Git Clone
```bash
mkdir -p /var/www/three-body-problem
cd /var/www/three-body-problem
git clone https://github.com/dnrdnsyh/three-body-problem.git
```



## 🚀 How to Run Applications

### 🐘 Laravel API (Port 8001)
```bash
cd laravel
composer install
php artisan key:generate
php artisan migrate --seed
php artisan serve
```

Add config for laravel host address and port
```bash
php artisan make:command CustomServeCommand
```

Delete the old config and replace with
```bash
<?php

namespace App\Console\Commands;

use Illuminate\Foundation\Console\ServeCommand;
use Symfony\Component\Console\Input\InputOption;

class CustomServeCommand extends ServeCommand
{
    /**
     * Get the console command options.
     *
     * @return array
     */
    protected function getOptions()
    {
        return [
        ['host', null, InputOption::VALUE_OPTIONAL, 'The host address to serve the application on.', '**192.168.56.49**'],
        ['port', null, InputOption::VALUE_OPTIONAL, 'The port to serve the application on.', **8001**],
        ['tries', null, InputOption::VALUE_OPTIONAL, 'The max number of ports to attempt to serve from', 10],
        ['no-reload', null, InputOption::VALUE_NONE, 'Do not reload the development server on .env file changes'],
        ];
    }
}
```

### 🐹 Go API (Port 8080)
```bash
cd go
go mod tidy
go run main.go
```

### ⚛️ React Frontend (Port 3000)
```bash
cd frontend
npm install
npm start
```

## 🌐 API Endpoints

Both Laravel and Go APIs provide identical endpoints:

- **GET** `/api/products` - Get all products
- **GET** `/api/products/{id}` - Get product by ID

## 🎯 Frontend Features

The React frontend provides:
- 🐘 **Laravel API Button** - Hits Laravel API at `http://127.0.0.1:8001`
- 🐹 **Go API Button** - Hits Go API at `http://localhost:8080`  
- 📊 **Real-time Data Display** - Shows API responses in formatted cards
- ❌ **Error Handling** - User-friendly error messages
- 📱 **Responsive Design** - Works on desktop and mobile

## 🔗 URLs

- **Laravel API:** http://127.0.0.1:8001/api/products
- **Go API:** http://localhost:8080/api/products  
- **React Frontend:** http://localhost:3000

## 🛠️ Tech Stack

- **Backend:** Laravel (PHP) + Go
- **Frontend:** React.js
- **Database:** MySQL (with SQLite fallback)
- **Styling:** CSS3 with gradients and animations

## ✅ Quick Test

Run all applications and test:

```bash
# Terminal 1: Laravel API
cd laravel && php artisan serve --port=8001

# Terminal 2: Go API  
cd go && go run main.go

# Terminal 3: React Frontend
cd frontend && npm start

# Terminal 4: Test APIs
./compare_apis.sh
```

Access frontend at http://localhost:3000 and click both API buttons to see the results!
