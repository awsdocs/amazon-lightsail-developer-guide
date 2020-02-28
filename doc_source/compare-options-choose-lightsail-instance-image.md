# Choose an Amazon Lightsail instance image<a name="compare-options-choose-lightsail-instance-image"></a>

 *Last updated: January 13, 2020* 

Lightsail provides several options for you to create your virtual private server\. This topic helps you decide which operating system \(OS\), application, or development stack is right for your project\. We organized the applications by functional area \(e\.g\., CMS and e\-Commerce\)\.

## Compare platforms<a name="compare-platforms"></a>

Lightsail has two platforms to choose from: Linux/Unix\-based or Windows\-based platforms\. If you already have an application in mind, you probably already have an OS platform picked out\. You can choose one of the following options to get started:
+  [Get started with Linux/Unix\-based instances in Lightsail](getting-started-with-amazon-lightsail.md) 
+  [Get started with Windows\-based instances in Lightsail](get-started-with-windows-based-instances-in-lightsail.md) 

## Compare operating systems<a name="compare-operating-systems"></a>

Lightsail has several operating systems to choose from\.

** **Windows Server 2016** **  
Unless you need to run Windows Server 2012 R2 for some reason, we recommend using the latest version of Windows Server 2016\.  
Lightsail running Windows Server is a fast and dependable environment for deploying applications using the Microsoft Web Platform\. Lightsail enables you to run any compatible Windows\-based solution on AWS' high\-performance, reliable, cost\-effective, cloud computing platform\. Common Windows use cases include Enterprise Windows\-based application hosting, website and web\-service hosting, data processing, media transcoding, distributed testing, ASP\.NET application hosting, and any other application requiring Windows software\.  
 [Learn more about the Windows Server 2016 image](https://aws.amazon.com/marketplace/pp/B01M7SJEU7) 

** **Windows Server 2012 R2** **  
Windows Server 2012 R2 is also available as a base operating system\. If you're migrating an application from somewhere else to Lightsail, and it's not compatible with Windows Server 2016, you may want to use this base OS instead\.  
You can use Windows Server 2012 R2 with the same use cases as listed under Windows Server 2016\.  
 [Learn more about the Windows Server 2012 R2 image](https://aws.amazon.com/marketplace/pp/B00KQOWCAQ) 

** **Amazon Linux 2018** **  
The Amazon Linux AMI is a supported and maintained Linux image provided by Amazon Web Services \(AWS\) for use on Lightsail and Amazon EC2\. It's designed to provide a stable, secure, and high\-performance execution environment for applications running on Lightsail\. It includes packages that enable easy integration with AWS, such as the AWS Command Line Interface \(AWS CLI\) and AWS API tools\. AWS provides ongoing security and maintenance updates to all instances running the Amazon Linux AMI\.  
[Learn more about the Amazon Linux AMI](https://aws.amazon.com/amazon-linux-ami/)

** **CentOS 7** **  
CentOS is a Linux distribution that provides a free, enterprise\-class, community\-supported computing platform functionally compatible with its upstream source, Red Hat Enterprise Linux\.  
[Learn more about CentOS](https://aws.amazon.com/marketplace/pp/B00O7WM7QW)\.

** **Debian 8 and 9** **  
Debian is a computer operating system composed of software packages released as free and open source software primarily under the GNU General Public License along with other free software licenses\. Debian GNU/Linux, which includes the GNU OS tools and Linux kernel, is a popular and influential Linux distribution\. It is distributed with access to repositories containing thousands of software packages ready for installation and use\.  
[Learn more about Debian](https://www.debian.org/doc/)\.

** **FreeBSD 12** **  
FreeBSD is an operating system used to power servers, desktops, and embedded systems\. Derived from BSD, the version of UNIX developed at the University of California, Berkeley, FreeBSD has been continually developed by a large community for more than 30 years\. FreeBSD's networking, security, storage, and monitoring features, including the pf firewall, the Capsicum and CloudABI capability frameworks, the ZFS filesystem, and the DTrace dynamic tracing framework, make FreeBSD the platform of choice for many of the busiest web sites and most pervasive embedded networking and storage systems\.  
[Learn more about FreeBSD](https://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/)\.

** **openSUSE 15\.1 Leap** **  
The openSUSE distribution is a stable, easy to use and complete multi\-purpose Linux distribution\. It is aimed towards users and developers working on the desktop or server\. It is great for beginners, experienced users and ultra geeks alike, in short, it is perfect for everybody\!  
[Learn more about openSUSE](https://www.opensuse.org/)\.

** **Ubuntu 16 and 18** **  
Ubuntu Server is a Debian\-based Linux operating system used for virtual servers\. A default installation of Ubuntu contains a wide range of software that includes LibreOffice, Firefox, Thunderbird, and Transmission\. You can install many additional software packages, such as Evolution, GIMP, Pidgin, and Synaptic by using the APT\-based package management tool \(`apt-get`\)\.  
[Learn more about Ubuntu](https://help.ubuntu.com/community/CommunityHelpWiki)\.

## Compare Database applications<a name="compare-database-applications"></a>

Lightsail has the following database application available:

** **SQL Server 2016 Express** **  
SQL Server Express is a relational database management system that is free to download, distribute and use\. It comprises a database specifically targeted for embedded and smaller\-scale applications\. This Lightsail image runs on a base OS of Windows Server 2016\.  
 [Learn more about the SQL Server Express image](https://aws.amazon.com/marketplace/pp/B01MAZHH98) 

## Compare CMS applications<a name="compare-cms-applications"></a>

Lightsail has three content management system \(CMS\) applications to choose from\. Each image uses Linux/Unix \(Ubuntu\) as the base operating system\.

** **WordPress certified by Bitnami** **  
Bitnami WordPress is a preconfigured, ready\-to\-use image for running WordPress on Lightsail\. WordPress is a popular web publishing platform for building blogs and websites\. You can customize it by using a wide selection of themes, extensions, plugins, and widgets\.  
 WordPress features a full theme system, which enables you to change the look and feel of your site with a few clicks\. You can also use existing free or commercial WordPress themes\. WordPress is in full compliance with the standards of the W3C\.   
[Learn more about the Bitnami WordPress application](https://bitnami.com/stack/wordpress)\.

** **WordPress Multisite certified by Bitnami** **  
WordPress Multisite enables administrators to host and manage multiple websites from the same WordPress instance\. These websites can all have unique domain names and can be customized by their owners, while sharing assets such as themes and plugins that are made available by the server admin\. Updates to all sites can be pushed at once, ensuring that they are always kept safe and secure\.  
WordPress Multisite is great for organizations such as universities, corporations, and agencies that need to enable many people to host their own websites while giving overall control to a central administrator\.  
[Learn more about the Bitnami WordPress Multisite application](https://bitnami.com/stack/wordpress-multisite)\.

** **Ghost certified by Bitnami** **  
Ghost is a publishing platform that is suitable for everything from personal blogs to major news websites\. Built on Node\.js, its modern technology stack makes it versatile and flexible for developers seeking to integrate with other applications and tools, while maintaining ease of use for content creators\.  
[Learn more about the Bitnami Ghost application](https://bitnami.com/stack/ghost)\.

** **Joomla\! certified by Bitnami** **  
Bitnami Joomla\! is a preconfigured, ready\-to\-use image for running Joomla\! on Lightsail\. Joomla\! is a CMS you can use to build a variety of websites or portals\. These include personal, corporate, small business, nonprofit, and other organizational websites\.  
Joomla\! also features a registration system that enables users to configure personal options\. Authentication is an important part of user management, and Joomla\! supports multiple protocols, including LDAP, OpenID, and others\. Joomla\! supports many different languages and offers guidance for using them for the website and the administration panel\. Also, the **Banner Manager** makes it easy to set up and manage banners on your site\. You can track metrics, including setting impression numbers, special URLs, and more\.   
[Learn more about the Bitnami Joomla\! application](https://bitnami.com/stack/joomla)\.

** **Drupal certified by Bitnami** **  
Bitnami Drupal is a preconfigured, ready\-to\-use image for running Drupal on Lightsail\. Drupal is a content management platform that enables users to easily publish, manage, and organize content\. It's used for community web portals, discussion sites, corporate websites, and more\. You can easily extend Drupal by plugging in modules\. Drupal is built for high performance, is scalable to many servers, and has easy integration with REST, JSON, SOAP, and other formats\.  
There are thousands of add\-on modules and designs available for Drupal free of charge\. Drupal is also available in multiple languages\.  
[Learn more about the Bitnami Drupal application](https://bitnami.com/stack/drupal)\.

## Compare application stacks and servers<a name="compare-application-stacks-servers"></a>

Lightsail has five application stacks and servers for a wide variety of development projects\. Each image uses Linux/Unix \(Ubuntu\) as the base operating system\.

** **LAMP stack \(PHP 7\) certified by Bitnami** **  
The Bitnami LAMP stack simplifies the development and deployment of PHP applications\. It includes ready\-to\-run versions of Apache, MySQL, PHP, and phpMyAdmin, as well as the other software required to run each of those components\. Bitnami LAMP stack is completely integrated and configured, so you'll be ready to start developing your application as soon as you create your instance in Lightsail\. Bitnami LAMP stack is regularly updated to ensure that you always have access to the latest stable releases for each bundled component\.  
[Learn more about the Bitnami LAMP stack](https://bitnami.com/stack/lamp)\.

** **Django certified by Bitnami** **  
Django is a high\-level Python Web framework that encourages rapid development and clean, pragmatic design\. Python is a dynamic object\-oriented programming language that can be used for many kinds of software development\. The Bitnami Django Stack greatly simplifies the deployment of Django and its runtime dependencies and includes ready\-to\-run versions of Python, Django, MySQL and Apache\.  
[Learn more about the Bitnami Django stack](https://bitnami.com/stack/django)\.

** **Node\.js certified by Bitnami** **  
Bitnami Node\.js is a preconfigured, ready\-to\-use image for running Node\.js on Lightsail\. Node\.js is a platform built on Chrome's JavaScript runtime for easily creating fast, scalable network applications\. It uses an event\-driven, nonblocking I/O model that makes it lightweight and efficient\. Node\.js is well suited for data\-intensive, real\-time applications\.  
[Learn more about the Bitnami Node\.js stack](https://bitnami.com/stack/nodejs)\.

** **MEAN stack certified by Bitnami** **  
Bitnami MEAN stack provides a complete development environment for MongoDB and Node\.js that you can deploy in one click\. It includes the latest stable release of MongoDB, Express, Angular, Node\.js, Git, PHP, and RockMongo\.  
[Learn more about the Bitnami MEAN stack](https://bitnami.com/stack/mean)\.

** **GitLab certified by Bitnami** **  
Bitnami Gitlab is a preconfigured, ready\-to\-use image for running GitLab on Lightsail\. GitLab is self\-hosted Git management software that is fast, secure, and based on Ruby on Rails\. GitLab CI \(also included\) is an open source Continuous Integration \(CI\) server closely integrated with Git and GitLab\.  
 GitLab enables you to keep your code secure on your own server, manage repositories, users, and access permissions\. It's self\-contained, so you can duplicate or move the installation to different servers easily\.   
[Learn more about the Bitnami GitLab stack](https://bitnami.com/stack/gitlab)\.

** **Nginx \(LEMP stack\) certified by Bitnami** **  
Bitnami Nginx Stack provides a complete PHP, MySQL, and Nginx development environment that you can launch in one click\. It also bundles phpMyAdmin, SQLite, ImageMagick, FastCGI, Memcache, GD, CURL, PEAR, PECL, and other components\.  
 Nginx is an asynchronous server and its main advantage is scalability\. The Nginx stack is also known as LEMP \(Linux, Nginx, MySQL, and PHP\)\.   
[Learn more about the Bitnami Nginx \(LEMP\) stack](https://bitnami.com/stack/nginx)\.

** **Plesk Hosting Stack on Ubuntu** **  
Build, secure, and run websites and applications on Lightsail and AWS using the Hosting Stack powered by Plesk\. This includes all your web\-based server management and security tools, plus WordPress automation in a graphical user interface\. It simplifies the work of web professionals and provides the scalability, security, and performance that your customers need\.  
 [Set up and configure Plesk on Lightsail](set-up-and-configure-plesk-stack-on-lightsail.md)   
[Learn more about the Plesk stack](https://docs.plesk.com/en-US/current/administrator-guide/about-plesk.70559/)\.

## E\-commerce applications in Lightsail<a name="compare-ecommerce-applications-in-lightsail"></a>

Lightsail currently has one e\-commerce application image: Magento\. This Magento image uses Linux/Unix \(Ubuntu\) as the base operating system\.

 **Magento certified by Bitnami**   
Bitnami Magento is a preconfigured, ready\-to\-use image for running Magento on Lightsail\. You can build engaging, responsive, and secure sites using Magento\. Magento is a feature\-rich, flexible e\-commerce solution that includes transaction options, multistore functionality, loyalty programs, product categorization, shopper filtering, promotion rules, and more\.  
You can use Magento to create a highly customized e\-commerce site that reflects your brand\. Magento integrates with your business operations, so you can manage your e\-commerce site as your business needs\.   
[Learn more about the Bitnami Magento stack](https://bitnami.com/stack/magento)\.

## Project management applications in Lightsail<a name="compare-project-management-applications-in-lightsail"></a>

Lightsail currently has one project management application image: Redmine\. This image uses Linux/Unix \(Ubuntu\) as the base operating system\.

 **Redmine certified by Bitnami**   
Bitnami Redmine is a preconfigured, ready\-to\-use image for running Redmine on Lightsail\. Redmine is a flexible project management web application\. It includes support for multiple projects, role\-based access control, Gantt chart and calendar, management of news, documents, and files, per\-project wikis and forums, SCM integration, and more\.  
[Learn more about the Bitnami Redmine stack](https://bitnami.com/stack/redmine)\.