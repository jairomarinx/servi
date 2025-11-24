# Servi  
A simple and practical marketplace for real world local services

## Overview  
Servi is an open project that aims to make it easier for people to offer local services and for others to hire them with confidence. Providers can create a service portfolio with photos, prices and descriptions. Customers can browse, compare and hire services in a few steps.

The goal is to reduce friction in everyday service needs while giving local talent a space to be visible and trusted.

## Key Features  
* Service provider registration  
* Portfolios with photos, descriptions and pricing  
* Urgent and scheduled service requests  
* Customer profiles with service history  
* Messaging system between customers and providers  
* Basic reputation and validation workflow  
* Focus on everyday local needs like  
  * Door installation  
  * Night time nursing for a few hours  
  * Appliance repair  
  * In home tutoring  

## Why this project  
Many cities have a large demand for daily services but very little digital organization. A lot of independent providers offer great work but lack access to platforms. Servi aims to help reduce this gap by providing a clean and simple marketplace that anyone can join.

## Tech Stack  
* Backend: Laravel  
* Frontend: Blade templates with Bootstrap  
* Database: MySQL or MariaDB  
* REST style API under development  
* Designed for clarity, performance and reliability

## Getting Started  
```bash
git clone https://github.com/youruser/servi.git
cd servi
composer install
cp .env.example .env
php artisan key:generate
php artisan migrate
php artisan serve
