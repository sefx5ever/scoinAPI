# SCoinAPI Documentation
## Package overview
The scoinAPI is a Python package providing fast, simplify, and to manage the role's authority. It aims to be a fundamental package to access the method of the SCoin system instead of writing a method without fully understood. Besides that, it's easy to get started in creating a role in the SCoin system. Also, This package will auto-update after the real API has been updated.

## Getting started
* ### What is scoinAPI ?
    The light package for SCU blockchain in the IOTA system.
* ### Who can use the scoinAPI ?
    The developer of SCoin system.
* ### How do I install the package ?
    Run the following command to install:
    ```python
    $ pip install SCoinAPI
    ```
* ### What is the role of the SCoin system ?
    There are three roles which are the central bank, bank, and retailer.
* ### What is the difference between each role ?
    Each role has a different authority to access the method.
* ### How can import the package ?
    To import the package based on the roles:
    * #### The Central Bank
    ```python
    from SCoinAPI import centralbank
    cb = centralbank.Central_Bank()
    ```
    * #### The Bank
    ```python
    from SCoinAPI import bank
    bk = bank.Bank()
    ```
    * #### The Retailer
    ```python
    from SCoinAPI import retailer
    rt = retailer.Retailer()
    ```
* ### What are the layer in SCoin system ?
    The layer in SCoin system means that the role of user.
    (a) layer 1 = the central bank
    (b) layer 2 = the bank or retailer 

## Each role's methods in the SCoin system
* ### The Central Bank
    * [connection_test](#connection_test)
    * [send_token](#send_token)
    * [get_balance](#get_balance)
    * [create_did](#create_did)
    * [get_did](#get_did)
    * [verify_token](#verify_token)
    * [send_token](#send_token)
    * [send_tokens](#send_tokens)
    * [remove_layer1](#remove_layer1)
    * [get_transactions_by_timestamp](#get_transactions_by_timestamp)
    * [get_user_by_timestamp](#get_user_by_timestamp)
    * [get_info](#get_info)
    * [set_central_bank](#set_central_bank)
    * get_all_cluster [ To be develop ]
    * bridge [ To be delete ]
    * snapshot [ To be delete ]
    * get_enseed [ To be develop ]

* ### The Bank
    * [connection_test](#connection_test)
    * [send_tokens](#send_token)
    * [get_balance](#get_balance)
    * [create_did](#create_did)
    * [get_did](#get_did)
    * [verify_token](#verify_token)
* ### The Retailer
    * [connection_test](#connection_test)
    * [send_tokens](#send_token)
    * [get_balance](#get_balance)

## API Reference
* ### connection_test
    - #### Description :
        To test the real API connection wether is serving.
    - #### Parameters :
        - l(str) : Optional,To set the real API link if it has been changed.
    - #### Returns :
        Dict of status and message.
    - #### Usage :
        ```python
        r = cb.connection_test()
        ```
* ### send_token
    - #### Description :
        To make transaction within two user of SCoin system,but it only available for layer 1 user did.
    - #### Parameters :
        - password(str) : The user's password.
        - sen(str) : The sender's username.
        - rev(str) : The receiver's username.
        - num(int) : The transaction amount.
        - method(str) : Optinal,The user method, default value is light.
        - description(any) : Optional,The metadata of transaction.
        - l(str) : Optional,To set the real API link if it has been changed.
    - #### Returns :
        Dict of status, response data and message.
    - #### Usage :
        ```python
        r = cb.send_token('SENDER_PASSWORD','SENDER','RECEIVABLE',20)
        ```
* ### send_tokens
    - #### Description :
        To make transaction within two user of SCoin system,it is available for basic transaction.
    - #### Parameters :
        - password(str) : The user's password.
        - sen(str) : The sender's username.
        - rev(str) : The receiver's username.
        - num(int) : The transaction amount.
        - method(str) : Optinal,The user method, default value is light.
        - description(any) : Optional,The metadata of transaction.
        - l(str) : Optional,To set the real API link if it has been changed.
    - #### Returns :
        Dict of status, response data and message.
    - #### Usage :
        ```python
        r = cb.send_token('SENDER_PASSWORD','SENDER','RECEIVABLE',20)
        ```
* ### get_balance
    - #### Description :
        To get the user's balance through the user's did.
    - #### Parameters :
        - name(str) : The user's did.
        - l(str) : Optional,To set the real API link if it has been changed.
    - #### Returns :
        Dict of status, response data and message.
    - #### Usage :
        ```python
        r = cb.get_balance('USERNAME')
        ```
* ### create_did
    - #### Description :
        To create an user did in the SCoin system.
    - #### Parameters :
        - name(str) : The user's did.
        - password(str) : The user's password.
        - method(str) : Optinal,The user method, default value is light.
        - description(any) : Optional,The metadata of transaction.
        - l(str) : Optional,To set the real API link if it has been changed.
        - pub_key(str) : Optional,RSA public key or endpoint, service will generate one key-pair if this field is empty.
    - #### Returns :
        Dict of status, response data and message.
    - #### Usage :
        ```python
        r = cb.create_did('DID','PASSWORD')
        ```
* ### get_did
    - #### Description :
        To get an user's did detail through hash value(pub_key).
    - #### Parameters :
        - hash_(str) : The public key of user's did. 
        - l(str) : Optional,To set the real API link if it has been changed.
    - #### Returns :
        Dict of status, response data and message.
    - #### Usage :
        ```python
        r = cb.get_did('HASH_VALUE')
        ```
* ### verify_token
    - #### Description :
        To verify self-token.
    - #### Parameters :
        - name(str) : The user's did.
        - password(str) : The user's password.
        - token(str) : The hash value of token to be verify.
        - l(str) : Optional,To set the real API link if it has been changed.
    - #### Returns :
        Dict of status and message.
    - #### Usage :
        ```python
        r = cb.verify_token('DID','PASSWORD','HASH_VALUE')
        ```
* ### remove_layer1
    - #### Description :
        To downgrade the authority of the user to layer-2.
    - #### Parameters :
        - name(str) : The user's did to be downgrade.
        - password(str) : The user's password to be downgrade.
        - l(str) : Optional,To set the real API link if it has been changed.
    - #### Returns :
        Dict of status and message.
    - #### Usage :
        ```python
        r = cb.remove_layer1('DID','PASSWORD','HASH_VALUE')
        ```
* ### get_transactions_by_timestamp
    - #### Description :
        To get the transaction during a specific time range.
    - #### Parameters :
        - start_time(int) : The start time.
        - end_time(int) : The end time.
        - l(str) : Optional,To set the real API link if it has been changed.
    - #### Returns :
        Dict of status, response data and message.
    - #### Usage :
        ```python
        r = cb.get_transactions_by_timestamp(0,10000000)
        ```
* ### get_user_by_timestamp
    - #### Description :
        To get the sign up user during a specific time range.
    - #### Parameters :
        - start_time(int) : The start time.
        - end_time(int) : The end time.
        - l(str) : Optional,To set the real API link if it has been changed.
    - #### Returns :
        Dict of status, response data and message.
    - #### Usage :
        ```python
        r = cb.get_user_by_timestamp(0,10000000)
        ```
* ### get_info
    - #### Description :
        To get the total number of sign up user.
    - #### Parameters :
        - l(str) : Optional,To set the real API link if it has been changed.
    - #### Returns :
        Dict of status, response data and message.
    - #### Usage :
        ```python
        r = cb.get_info()
        ```
* ### set_central_bank
    - #### Description :
        To upgrade the authority of the user to layer-1.
    - #### Parameters :
        - name(str) : The user's did to be upgrade.
        - password(str) : The user's password to be upgrade.
        - l(str) : Optional,To set the real API link if it has been changed.
    - #### Returns :
        Dict of status and message.
    - #### Usage :
        ```python
        r = cb.set_central_bank('DID','PASSWORD')
        ```

## If you have any issues, please contact the information below.
* LINE  : nus_jie
* Email : sefx5ever@gmail.com