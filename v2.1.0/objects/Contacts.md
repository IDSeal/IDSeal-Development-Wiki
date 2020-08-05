# Contact
Contacts are the primary object in the system. Essentially all actions are performed through or with a Contact 
Object and most other objects can reference back to a their origin Contact.

Contacts represent customers which can take on many forms:
 - IBO Enrollee
 - Normal Customer
 - Employee
 - Company POC
 - Contact Personal Association (Family)


## Database Schema

```
#!mysql

CREATE TABLE `contacts` (
  `id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
  `stage` varchar(255) DEFAULT NULL,
  `first_name` varchar(255) DEFAULT NULL,
  `last_name` varchar(255) DEFAULT NULL,
  `title` varchar(255) DEFAULT NULL,
  `company` varchar(255) DEFAULT NULL,
  `email` varchar(255) DEFAULT NULL,
  `password` varchar(255) DEFAULT NULL,
  
  `phonenumber` varchar(255) DEFAULT NULL,
  `address` varchar(255) DEFAULT NULL,
  `address2` varchar(255) DEFAULT NULL,
  `city` varchar(255) DEFAULT NULL,
  `state` varchar(255) DEFAULT NULL,
  `country` varchar(255) DEFAULT NULL,
  `zip` varchar(255) DEFAULT NULL,
  
  `ibo_number` varchar(255) DEFAULT NULL,
  
  `activation_status` varchar(255) DEFAULT NULL,
  `account_status` varchar(255) DEFAULT NULL,
  `acn_account_status` varchar(255) DEFAULT NULL,
  `experian_account_status` varchar(255) DEFAULT NULL,
  
  `client_ip` varchar(255) DEFAULT NULL,
  `environment` varchar(255) DEFAULT 'development',
  
  `product_id` varchar(255) DEFAULT NULL,
  `ontraport_product_acn_id` varchar(255) DEFAULT NULL,
  
  `referral_page` varchar(255) DEFAULT NULL,
  
  `ontraport_contact_id` varchar(255) DEFAULT NULL,
  `experian_subscriber_number` varchar(255) DEFAULT NULL,
  `acn_contact_id` varchar(255) DEFAULT NULL,
  `csi_contact_id` varchar(255) DEFAULT NULL,
  
  `authnet_customer_id` varchar(255) DEFAULT NULL,
  `authnet_customer_profile_id` varchar(255) DEFAULT NULL,
  `authnet_customer_payment_id` varchar(255) DEFAULT NULL,
  `authnet_customer_subcription_id` varchar(255) DEFAULT NULL,
  `authnet_transaction_authorization` varchar(255) DEFAULT NULL,
  `authnet_transaction_id` varchar(255) DEFAULT NULL,
  
  `data` text,
  
  `is_authorized` tinyint(1) DEFAULT '0',
  `is_transacted` tinyint(1) DEFAULT '0',
  `is_ontraport_contact` tinyint(1) DEFAULT '0',
  `is_enrolled` tinyint(1) DEFAULT '0',
  `is_authenticated` tinyint(1) DEFAULT '0',
  `employer_contact_id` varchar(255) DEFAULT NULL,
  `is_cancelled` tinyint(1) DEFAULT '0',
  `is_employer` tinyint(1) DEFAULT '0',
  `is_employee` tinyint(1) DEFAULT '0',
  
  `created` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  `updated` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1;
```


## Core Properties

```
#!php
array(
    'id' => array(
        'type' => 'numeric',
        'name' => 'ID',
        'label' => 'Contact ID',
        'defaultListed' => true,
        'listDisplay' => 'viewObjectLink',
        'viewDisplayCategory' => 'primary',
        'editable' => false,
        'source' => 'core',
    ),
    'stage' => array(
        'type' => 'string',
        'name' => 'Stage',
        'label' => 'Stage',
        'defaultListed' => true,
        'listDisplay' => 'viewObjectLink',
        'viewDisplayCategory' => 'primary',
        'editable' => false,
        'searchable' => true,
        'searchableKey' => 'stage',
        'source' => 'core',
    ),
    'name' => array(
        'type' => 'string',
        'name' => 'Full Name',
        'label' => 'Full Name',
        'defaultListed' => true,
        'posttransformers' => 'namePostTransformer',
        'listDisplay' => 'viewObjectLink',
        'editable' => false,
        'source' => 'user',
        
    ),
    'firstName' => array(
        // 'type' => 'string',
        'name' => 'First Name',
        'label' => 'First Name',
        'viewDisplayCategory' => 'details',
        'required' => true,
        'type' => 'name',
        'minLength' => 2,
        'maxLength' => 128,
        'searchable' => true,
        'searchableKey' => 'first_name',

    ),
    'lastName' => array(
        // 'type' => 'string',
        'name' => 'Last Name',
        'label' => 'Last Name',
        'viewDisplayCategory' => 'details',
        'required' => true,
        'type' => 'name',
        'minLength' => 2,
        'maxLength' => 128,
        'searchable' => true,
        'searchableKey' => 'last_name',

    ),
    
    'password' => array(
        'type' => 'password',
        'name' => 'Password',
        // 'required' => true, // Required is turned off because Business Direct will create contacts without pw
        'label' => 'Password',
        'viewDisplayCategory' => 'details',
        'editDisplaySpecialDisplay' => 'confirm',
        'bypassValidationIfEmpty' => true,
        
    ),
    
    'email' => array(
        'type' => 'email',
        'name' => 'Email',
        'label' => 'Email',
        'defaultListed' => true,
        'viewDisplayCategory' => 'details',
        'required' => true,
        'searchable' => true,
        'searchableKey' => 'email',

        
    ),
    'address' => array(
        'type' => 'string',
        'name' => 'Address',
        'label' => 'Address',
        'viewDisplayCategory' => 'details',
        'required' => true,
        'minLength' => 2,
        'maxLength' => 128,
        'searchable' => true,
        'searchableKey' => 'address',

    ),
    'address2' => array(
        'type' => 'string',
        'name' => 'Address2',
        'label' => 'Address2',
        'viewDisplayCategory' => 'details',
        'maxLength' => 128,
    ),
    'city' => array(
        'type' => 'string',
        'name' => 'City',
        'label' => 'City',
        'viewDisplayCategory' => 'details',
        'required' => true,
        'minLength' => 2,
        'maxLength' => 128,
        'searchable' => true,
        'searchableKey' => 'city',

    ),
    'state' => array(
        'type' => 'string',
        'name' => 'State',
        'label' => 'State',
        'viewDisplayCategory' => 'details',
        'fixedLength' => 2,
        'required' => true,
        'searchable' => true,
        'searchableKey' => 'state',

        
    ),
    'zip' => array(
        'type' => 'string',
        'name' => 'Zip',
        'label' => 'Zip',
        'viewDisplayCategory' => 'details',
        'required' => true,
        'pretransformers' => 'numeric',
        'minLength' => 5,
        'maxLength' => 10,
        'searchable' => true,
        'searchableKey' => 'zip',

    ),
    
    'country' => array(
        'type' => 'string',
        'name' => 'Country',
        'label' => 'Country',
        'viewDisplayCategory' => 'details',
        'minLength' => 2,
        'maxLength' => 128,
        'default' => 'USA',
    ),
    
    'company' => array(
        'type' => 'string',
        'name' => 'Company',
        'label' => 'Company',
        'viewDisplayCategory' => 'details',
        'minLength' => 2,
        'maxLength' => 128,
        'default' => '',
    ),
    
    'title' => array(
        'type' => 'string',
        'name' => 'Title',
        'label' => 'Title',
        'viewDisplayCategory' => 'details',
        'minLength' => 2,
        'maxLength' => 128,
        'default' => '',
        'searchable' => true,
        'searchableKey' => 'title',

    ),
    
    'phoneNumber' => array(
        'type' => 'string',
        'name' => 'Phone Number',
        'label' => 'Phone Number',
        'viewDisplayCategory' => 'details',
        
        'required' => true,
        'pretransformers' => 'numeric',
        'posttransformers' => 'numeric',
        'fixedLength' => 10,
        'searchable' => true,
        'searchableKey' => 'phonenumber',

    ),
    'officePhone' => array(
        'type' => 'string',
        'name' => 'Office Phone',
        'label' => 'Office Phone',
        'viewDisplayCategory' => 'details',
        
        'required' => true,
        'pretransformers' => 'numeric',
        'posttransformers' => 'numeric',
        'fixedLength' => 10,
    ),
    'IBONumber' => array(
        'type' => 'alphanumeric',
        'name' => 'IBO Number',
        'label' => 'IBO Number',
        'defaultListed' => true,
        
        'required' => true,
        'maxLength' => 128,
        'default' => '',
        'searchable' => true,
        'searchableKey' => 'ibo_number',

    ),
    'productBundle' => array(
        'type' => 'string',
        'name' => 'Product Bundle Number',
        'label' => 'Product Bundle Number',
        'viewDisplayCategory' => 'details',
        'posttransformers' => 'productBundlePostTransformer',
    ),
    
    'activationStatus' => array(
        'default' => '',
        'type' => 'string',
        'name' => 'Activation Status',
        'label' => 'Activation Status',
    ),
    
    'accountStatus' => array(
        'type' => 'string',
        'name' => 'Account Status',
        'label' => 'Account Status',
        'defaultListed' => true,
    ),
    
    'acnAccountStatus' => array(
        'type' => 'string',
        'name' => 'ACN Account Status',
        'label' => 'ACN Account Status',
        'defaultListed' => true,
    ),
    
    'experianAccountStatus' => array(
        'type' => 'string',
        'name' => 'Experian Account Status',
        'label' => 'Experian Account Status',
        'defaultListed' => true,
    ),
    
    'vipErrorReport' => array(
        'type' => 'string',
        'name' => 'VIP Error Report',
        'label' => 'VIP Error Report',
    ),
    'experianAuthenticationResult' => array(
        'type' => 'string',
        'name' => 'Experian Authentication Result',
        'label' => 'Experian Authentication Result',
    ),
    'experianErrorReport' => array(
        'type' => 'string',
        'name' => 'Experian Error Report',
        'label' => 'Experian Error Report',
    ),
    
    'lastTransactionTotal' => array(
        'type' => 'string',
        'name' => 'Last Transaction Total',
        'label' => 'Last Transaction Total',
        'posttransformers' => 'lastTransactionTotalPostTransformer',
        
    ),
    'lastTransactionTax' => array(
        'type' => 'string',
        'name' => 'Last Transaction Tax',
        'label' => 'Last Transaction Tax',
        'posttransformers' => 'lastTransactionTaxPostTransformer',
    ),
    
    'homeSupportLastTransactionTotal' => array(
        'type' => 'string',
        'name' => 'Last Home Support Transaction Total',
        'label' => 'Last Home Support Transaction Total',
        'posttransformers' => 'homeSupportLastTransactionTotalPostTransformer',
        
    ),
    'homeSupportLastTransactionTax' => array(
        'type' => 'string',
        'name' => 'Last Home Support Transaction Tax',
        'label' => 'Last Home Support Transaction Tax',
        'posttransformers' => 'homeSupportLastTransactionTaxPostTransformer',
    ),
    
    
    'lastCreditCardStatus' => array(
        'type' => 'string',
        'name' => 'Last Credit Card Status',
        'label' => 'Last Credit Card Status',
    ),
    
    
    
    
    'referralPage' => array(
        'type' => 'string',
        'name' => 'Referral Page',
        'label' => 'Referral Page',
        'viewDisplayCategory' => 'details',
        'editable' => false,
        
        'required' => true,
        'minLength' => 7,
        'maxLength' => 255,
        'default' => 'https://www.idseal.com/',
    ),
    
    'ontraportUniqueID' => array(
        'type' => 'string',
        'name' => 'Ontraport Unique ID',
        'label' => 'Ontraport Unique ID',
    ),
    
    'clientIP' => array(
        'type' => 'string',
        'name' => 'Client IP',
        'label' => 'Client IP',
        'viewDisplayCategory' => 'details',
        'editable' => false,
    ),
    'environment' => array(
        'type' => 'string',
        'name' => 'Environment',
        'label' => 'Environment',
        'viewDisplayCategory' => 'details',
        'editable' => false,
        'posttransformers' => 'environmentPostTransformer',
    ),
    
    
    'productID' => array(
        'type' => 'string',
        'name' => 'Product',
        'label' => 'Product',
        'linked' => true,
        'defaultListed' => true,
        'viewDisplayCategory' => 'peripherals',
        'viewDisplayPosition' => 'idseal',
        'editable' => false,
        'watchedByFields' => array('ontraportProductID', 'experianProductID', 'productBundle'),
        'searchable' => true,
        'searchableKey' => 'product_id',

    ),
    'ontraportProductID' => array(
        'posttransformers' => 'ontraportProductIDPostTransformer',
    ),
    
    'ontraportContactID' => array(
        'type' => 'string',
        'name' => 'Ontraport Contact ID',
        'label' => 'Ontraport Contact ID',
        'defaultListed' => true,
        'viewDisplayCategory' => 'peripherals',
        'viewDisplayPosition' => 'ontraport',
    ),
    'experianContactID' => array(
        'type' => 'string',
        'name' => 'Subscriber ID',
        'label' => 'Subscriber ID',
        'defaultListed' => true,
        'viewDisplayCategory' => 'peripherals',
        'viewDisplayPosition' => 'experian',
    ),
    'acnContactID' => array(
        'type' => 'string',
        'name' => 'ACN Contact ID',
        'label' => 'ACN Contact ID',
        'defaultListed' => true,
        'viewDisplayCategory' => 'peripherals',
        'viewDisplayPosition' => 'acn',
    ),
    
    'homeSupportProduct' => array(
        'type' => 'string',
        'name' => 'Home Support Product Bundle',
        'label' => 'Home Support Product Bundle',
        'viewDisplayCategory' => 'peripherals',
        'viewDisplayPosition' => 'ontraport',
    ),
    
    'homeSupportStatus' => array(
        'type' => 'string',
        'name' => 'Home Support Status',
        'label' => 'Home Support Status',
        'viewDisplayCategory' => 'peripherals',
        'viewDisplayPosition' => 'ontraport',
    ),
    
    /**
     * This is the ACN/VIP -> Product Type field in Ontraport.
     */
    'ontraportProductACNID' => array(
        'type' => 'string',
        'name' => 'Ontraport Product ACN ID',
        'label' => 'Ontraport Product ACN ID',
        'viewDisplayCategory' => 'peripherals',
        'viewDisplayPosition' => 'ontraport',
    ),
    
    'experianProductID' => array(
        'posttransformers' => 'experianProductIDPostTransformer',
    ),
    'acnProductID' => array(
        'posttransformers' => 'acnProductIDPostTransformer',
    ),
    'productType' => array(
        'posttransformers' => 'productTypePostTransformer',
    ),
    'billingZip' => array(
        'posttransformers' => 'billingZipPostTransformer',
    ),
    
    'nextBillingDate' => array(
        'type' => 'string',
        'name' => 'Next Billing Date',
        'label' => 'Next Billing Date',
        'viewDisplayCategory' => 'peripherals',
        'viewDisplayPosition' => 'ontraport',
    ),
    
    
    'enrollmentDate' => array(
        'type' => 'string',
        'name' => 'Enrollment Date',
        'label' => 'Enrollment Date',
        'viewDisplayCategory' => 'peripherals',
        'viewDisplayPosition' => 'ontraport',
    ),
    
    
    'is_authorized' => array(
        'type' => 'bool',
        'name' => 'Authorized',
        'label' => 'Authorized',
        'defaultListed' => true,
        'listDisplay' => 'objectType',
        'viewDisplayCategory' => 'primary',
    ),
    'is_transacted' => array(
        'type' => 'bool',
        'name' => 'Transacted',
        'label' => 'Transacted',
        'defaultListed' => true,
        'listDisplay' => 'objectType',
        'viewDisplayCategory' => 'primary',
    ),
    'is_enrolled' => array(
        'type' => 'bool',
        'name' => 'Enrolled',
        'label' => 'Enrolled',
        'defaultListed' => true,
        'listDisplay' => 'objectType',
        'viewDisplayCategory' => 'primary',
    ),
    'is_authenticated' => array(
        'type' => 'bool',
        'name' => 'Authenticated',
        'label' => 'Authenticated',
        'defaultListed' => true,
        'listDisplay' => 'objectType',
        'viewDisplayCategory' => 'primary',
    ),
    
    'is_cancelled' => array(
        'type' => 'bool',
        'name' => 'Cancelled',
        'label' => 'Cancelled',
        'defaultListed' => true,
        'listDisplay' => 'objectType',
        'viewDisplayCategory' => 'primary',
    ),
    
    'is_employer' => array(
        'type' => 'bool',
        'name' => 'Employer',
        'label' => 'Employer',
        'viewDisplayCategory' => 'primary',
    ),
    
    'is_employee' => array(
        'type' => 'bool',
        'name' => 'Employee',
        'label' => 'Employee',
        'viewDisplayCategory' => 'primary',
    ),
    
    'employerContactID' => array(
        'type' => 'string',
        'name' => 'Employer Contact ID',
        'label' => 'Employer Contact ID',
        'linked' => true,
        'defaultListed' => true,
        'viewDisplayCategory' => 'peripherals',
        'viewDisplayPosition' => 'idseal',
        'editable' => false,
    ),
    
    'employerOntraportContactID' => array(
        'posttransformers' => 'employerOntraportContactIDPostTransformer',
    ),
    
    
    'data' => array(
        'type' => 'json',
        'default' => '[]',
        'name' => 'Data',
        'label' => 'Data',
        'defaultListed' => true,
        'listDisplay' => 'json',
        'pretransformers' => 'ObjectToString',
        'posttransformers' => 'StringToObject',
        'viewDisplayCategory' => 'details',
    ),
    
    'created' => array(
        'type' => 'string',
        'name' => 'Created',
        'label' => 'Created',
        'defaultListed' => true,
        'listDisplay' => 'date',
        'viewDisplayCategory' => 'primary',
    ),
    'updated' => array(
        'type' => 'string',
        'name' => 'Updated',
        'label' => 'Updated',
        'defaultListed' => true,
        'listDisplay' => 'date',
        'viewDisplayCategory' => 'primary',
    ),
    
);
```



# Peripherals

## IDSeal



## Ontraport