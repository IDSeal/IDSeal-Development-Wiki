# Brief
Contacts are the primary object in the system. Essentially all actions are performed through or with a Contact 
Object and most other objects can reference back to a their origin Contact.

Contacts represent customers which can take on many forms:
 - IBO Enrollee
 - Normal Customer
 - Employee
 - Company POC
 - Contact Personal Association (Family)

## Properties

- id:
    - type: numeric
    - name: ID
    - label: Contact ID

- stage:
    - type: string
    - name: Stage
    - label: Stage

- name:
    - type: string
    - name: Full Name
    - label: Full Name

- firstName:
    // type: string
    - name: First Name
    - label: First Name
    - required: true
    - type: name
    - minLength: 2
    - maxLength: 128


- lastName:
    // 'type: string
    - name: Last Name
    - label: Last Name
    - required: true
    - type: name
    - minLength: 2
    - maxLength: 128


        
- password:
    - type: password
    - name: Password
    - required: true // Required is turned off because Business Direct will create contacts without pw
    - label: Password

        
- email:
    - type: email
    - name: Email
    - label: Email
    - required: true

- address:
    - type: string
    - name: Address
    - label: Address
            
    - required: true
            
    - minLength: 2
    - maxLength: 128


- address2:
    - type: string
    - name: Address2
    - label: Address2
            
    - maxLength: 128
            

- city:
    - type: string
    - name: City
    - label: City
            
    - required: true
    - minLength: 2
    - maxLength: 128


- state:
    - type: string
    - name: State
    - label: State
            
    - fixedLength: 2
    - required: true

            

- zip:
    - type: string
    - name: Zip
    - label: Zip
            
    - required: true
            
    - minLength: 5
    - maxLength: 10


        
- country:
    - type: string
    - name: Country
    - label: Country
    - minLength: 2
    - maxLength: 128
    - default: USA

        
- company:
    - type: string
    - name: Company
    - label: Company
    - minLength: 2
    - maxLength: 128
    - default: 

        
- title:
    - type: string
    - name: Title
    - label: Title
    - minLength: 2
    - maxLength: 128
    - default: 


        
- phoneNumber:
    - type: string
    - name: Phone Number
    - label: Phone Number
            
    - required: true
    - fixedLength: 10


- officePhone:
    - type: string
    - name: Office Phone
    - label: Office Phone
            
    - required: true
    - fixedLength: 10

- IBONumber:
    - type: alphanumeric
    - name: IBO Number
    - label: IBO Number
            
    - required: true
    - maxLength: 128
    - default: 


- productBundle:
    - type: string
    - name: Product Bundle Number
    - label: Product Bundle Number

        
- activationStatus:
    - default: 
    - type: string
    - name: Activation Status
    - label: Activation Status

        
- accountStatus:
    - type: string
    - name: Account Status
    - label: Account Status

        
- acnAccountStatus:
    - type: string
    - name: ACN Account Status
    - label: ACN Account Status

        
- experianAccountStatus:
    - type: string
    - name: Experian Account Status
    - label: Experian Account Status

        
- vipErrorReport:
    - type: string
    - name: VIP Error Report
    - label: VIP Error Report

- experianAuthenticationResult:
    - type: string
    - name: Experian Authentication Result
    - label: Experian Authentication Result

- experianErrorReport:
    - type: string
    - name: Experian Error Report
    - label: Experian Error Report

        
- lastTransactionTotal:
    - type: string
    - name: Last Transaction Total
    - label: Last Transaction Total
            

- lastTransactionTax:
    - type: string
    - name: Last Transaction Tax
    - label: Last Transaction Tax

        
- homeSupportLastTransactionTotal:
    - type: string
    - name: Last Home Support Transaction Total
    - label: Last Home Support Transaction Total
            

- homeSupportLastTransactionTax:
    - type: string
    - name: Last Home Support Transaction Tax
    - label: Last Home Support Transaction Tax

        
        
- lastCreditCardStatus:
    - type: string
    - name: Last Credit Card Status
    - label: Last Credit Card Status

        
        
        
        
- referralPage:
    - type: string
    - name: Referral Page
    - label: Referral Page
            
    - required: true
    - minLength: 7
    - maxLength: 255
    - default: https://www.idseal.com/

        
- ontraportUniqueID:
    - type: string
    - name: Ontraport Unique ID
    - label: Ontraport Unique ID

        
- clientIP:
    - type: string
    - name: Client IP
    - label: Client IP

- environment:
    - type: string
    - name: Environment
    - label: Environment

        
        
- ontraportProductID:

        
- ontraportContactID:
    - type: string
    - name: Ontraport Contact ID
    - label: Ontraport Contact ID

- experianContactID:
    - type: string
    - name: Subscriber ID
    - label: Subscriber ID

- acnContactID:
    - type: string
    - name: ACN Contact ID
    - label: ACN Contact ID

        
- homeSupportProduct:
    - type: string
    - name: Home Support Product Bundle
    - label: Home Support Product Bundle

        
- homeSupportStatus:
    - type: string
    - name: Home Support Status
    - label: Home Support Status

        
        /**
         * This is the ACN/VIP -> Product Type field in Ontraport.
         */
- ontraportProductACNID:
    - type: string
    - name: Ontraport Product ACN ID
    - label: Ontraport Product ACN ID

        
- experianProductID:

- acnProductID:

- productType:

- billingZip:

        
- nextBillingDate:
    - type: string
    - name: Next Billing Date
    - label: Next Billing Date

        
        
- enrollmentDate:
    - type: string
    - name: Enrollment Date
    - label: Enrollment Date

        
        
- is_authorized:
    - type: bool
    - name: Authorized
    - label: Authorized
    - listDisplay: objectType

- is_transacted:
    - type: bool
    - name: Transacted
    - label: Transacted
    - listDisplay: objectType

- is_enrolled:
    - type: bool
    - name: Enrolled
    - label: Enrolled
    - listDisplay: objectType

- is_authenticated:
    - type: bool
    - name: Authenticated
    - label: Authenticated
    - listDisplay: objectType

        
- is_cancelled:
    - type: bool
    - name: Cancelled
    - label: Cancelled
    - listDisplay: objectType

        
- is_employer:
    - type: bool
    - name: Employer
    - label: Employer

        
- is_employee:
    - type: bool
    - name: Employee
    - label: Employee

        
- employerContactID:
    - type: string
    - name: Employer Contact ID
    - label: Employer Contact ID
    - linked: true

        
- employerOntraportContactID:

        
        
- data:
    - type: json
    - default: []
    - name: Data
    - label: Data
    - listDisplay: json

        
- created:
    - type: string
    - name: Created
    - label: Created
    - listDisplay: date

- updated:
    - type: string
    - name: Updated
    - label: Updated
    - listDisplay: date
