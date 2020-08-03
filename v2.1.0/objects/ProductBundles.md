# Product Bundle


## Database Representation

```
CREATE TABLE `product_bundles` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `name` varchar(255) DEFAULT NULL,
  `subtitle` varchar(255) DEFAULT NULL,
  `description` varchar(510) DEFAULT "",
  `key` varchar(255) DEFAULT NULL,
  
  `code` varchar(255) DEFAULT NULL,
  `reference_code` varchar(255) DEFAULT NULL,
  `discount` varchar(255) DEFAULT NULL,
  
  `data` text,
  
  `experian_id` varchar(255) DEFAULT NULL,
  `acn_id` varchar(255) DEFAULT NULL,
  `ontraport_id` varchar(255) DEFAULT NULL,
  `ontraport_field_id` varchar(255) DEFAULT NULL,
  
  `created` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  `updated` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1;
```

## Properties

