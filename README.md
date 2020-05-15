# Technical Debt Tracking in Large Scale Organizations

A free Technical Debt Tracker adopted with Redmine.

![The MIT License](https://img.shields.io/badge/license-MIT-584492.svg) [![JavaScript Style Guide](https://img.shields.io/badge/code%20style-standard-brightgreen.svg)](http://standardjs.com/) [![Build Status](https://img.shields.io/endpoint.svg?url=https://actions-badge.atrox.dev/mrliptontea/PurpleMine2/badge&label=lint&logo=none)](https://actions-badge.atrox.dev/mrliptontea/PurpleMine2/goto) [![Issues](https://img.shields.io/github/issues/mrliptontea/PurpleMine2.svg)](https://github.com/mrliptontea/PurpleMine2/issues)

---

![Tasks](https://github.com/aldokhayel/Redmine_TrackingTD/blob/master/images/Tasks.png)

Compatible with Redmine 3.0+ and browsers: IE10+/Edge, latest Firefox and Google Chrome (others were not tested).


## Overview

I proposed a project management-based approach to track **technical debt**. The proposed system stands on a technical debt tracking methodology that adopts with [Redmine](https://www.redmine.org) -*project management system*-, to have the ability to track and manage current tasks and technical debt. 

I applied the attributes and metrics that was defined to track it easily and generating the reports based on the criteria. The metrics will support the project managers to ensure tracking the technical debt. Last, the project manager can generate the technical debt report. 


There are ten categories of the technical debts:
* Architecture Debt
* Code Debt
* Design Debt
* Documentation Debt
* Infrastructure Debt
* Resources Debt
* Requirement Debt
* Service Debt
* Process Debt
* Test Debt

## Mac Installation

* **Install Brew & Git**
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
```
brew install git
```
* **Install and Setup MySQL (5.7.19)**

```
brew install mysql
```
```
mysql.server start           # start mysql server
mysqladmin -u root password  # enter your new passowrd at first time
mysql -u root -p             # login MySQL with password
```
```
CREATE DATABASE redmine CHARACTER SET utf8mb4;
CREATE USER 'redmine'@'localhost' IDENTIFIED BY 'my_password';
GRANT ALL PRIVILEGES ON redmine.* TO 'redmine'@'localhost';          # login MySQL with password
```
* **MySQL Configuration**

Clone the project in your machine `Redmine_TrackingTD`:
```
git clone https://github.com/aldokhayel/Redmine_TrackingTD.git
```
Copy `config/database.yml.example` to `config/database.yml` and edit this file in order to configure your database settings for `production environment`.

```
cp config/database.yml.example config/database.yml
```

Update the `config/database.yml` file:

```
production:
  adapter: mysql2
  database: redmine
  host: localhost
  username: root
  password: {yourpassword}
  encoding: utf8mb4
``` 


* **Run Bundle**
```
sudo gem install bundler
 
# execute under redmine's folder
bundle install --without development test
bundle exec rake generate_secret_token
RAILS_ENV=production bundle exec rake db:migrate
RAILS_ENV=production bundle exec rake redmine:load_default_data
``` 

* **Run Application**
```
mysql.server restart
bundle exec rails server webrick -e production -p 5432  # port 5432
``` 

## Screenshots
### Status
![Main Page](https://github.com/aldokhayel/Redmine_TrackingTD/blob/master/images/Status.png)

### Main Page
![Main Page](https://github.com/aldokhayel/Redmine_TrackingTD/blob/master/images/Index.png)

### Technical Debt
![Technical Debt](https://github.com/aldokhayel/Redmine_TrackingTD/blob/master/images/TDs.png)

### Gantt Chart
![Gantt Chart](https://github.com/aldokhayel/Redmine_TrackingTD/blob/master/images/Gantt.png)


