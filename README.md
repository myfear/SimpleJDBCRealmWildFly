JDBC Realm and Form Based Authentication with GlassFish 3.1.2.2 and Primefaces 3.4
======================

Source for this blog-post:
http://blog.eisele.net/2013/01/jdbc-realm-glassfish312-primefaces342.html


http://wildfly.org/news/2014/02/06/GlassFish-to-WildFly-migration/


http://larmic.blogspot.de/2013/08/jaas-im-jboss-7x-bzw-eap-61.html

http://docs.oracle.com/javase/8/docs/technotes/guides/security/StandardNames.html#MessageDigest

https://docs.jboss.org/author/display/WFLY8/Security+subsystem+configuration

D:\wildfly-8.2.0.Final>java -cp d:\wildfly-8.2.0.final\modules\system\layers\base\org\picketbox\main\picketbox-4.0.21.Final.jar org.jboss.security.Base64Encoder admin SHA-512
D:\wildfly-8.2.0.Final>java -cp d:\wildfly-8.2.0.final\modules\system\layers\base\org\picketbox\main\picketbox-4.0.21.Final.jar org.jboss.security.Base64Encoder admin SHA-256
[x61Ey612Kl2gpFL56FT9weDnpSo4AV8j8+qx2AuTHdRyY036xxzTTrw10Wq3+4qQyB+XURPWx1ON
xp3Y3pB37A==]

D:\wildfly-8.2.0.Final>



CREATE TABLE `User` (  
  `id` bigint(20) NOT NULL,  
  `email` varchar(255) NOT NULL,  
  `firstName` varchar(255) NOT NULL,  
  `lastName` varchar(255) NOT NULL,  
  `password` varchar(255) NOT NULL,  
  PRIMARY KEY (`id`)  
)  


CREATE TABLE `Role` (  
  `id` bigint(20) NOT NULL,  
  `email` varchar(255) NOT NULL,  
  `role` varchar(255) DEFAULT NULL,  
  `user_id` bigint(20) DEFAULT NULL,  
  PRIMARY KEY (`id`),  
  KEY `u_user_id` (`user_id`),  
  CONSTRAINT `u_user_id` FOREIGN KEY (`user_id`) REFERENCES `User` (`id`)  
)   


INSERT INTO `wildfly`.`user` (`id`, `email`, `firstName`, `lastName`, `password`) VALUES ('1', 'markus@eisele.net', 'Markus', 'Eisele', 'jGl25bVBBBW96Qi9Te4V37Fnqchz/Eu4qB9vKrRIqRg=');

INSERT INTO `wildfly`.`role` (`id`, `email`, `role`, `user_id`) VALUES ('1', 'markus@eisele.net', 'ADMIN', '1');
