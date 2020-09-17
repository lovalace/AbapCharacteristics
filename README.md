# AbapCharacteristics
Dynamically add characteristics to internal table by customizing

## Tables structure
I created 2 tables, header and item<br>
#### ZXXT001 ->Header <br>
MANDT   <br>
PROGRAMNAME <br>

#### ZXXT002 --> Item<br>
MANDT<br>
PROGRAMNAME<br>
ATINN<br>

#### ZXXT002_V --> And I Created Maintance view Join with cabn and cabnt tables <br>
MANDT <br>
PROGRAMNAME <br>
ATINN <br>
ATFOR <br>
ANZST <br>
ANZDZ <br>
ATBEZ <br>


## Cluster view
![alt text](https://github.com/lovalace/AbapCharacteristics/blob/master/images/image.png?raw=true)
![alt text](https://github.com/lovalace/AbapCharacteristics/blob/master/images/image2.PNG?raw=true)

## Code Sample
     "Get Any data
     DATA(lt_stock) = cl_businessLayer=>if_stock~get_data( parameters = parameters ).
     "Add Characteristics dynamicall
     DATA(Result) = zcl_sd_characteristics=>add_characteristics( EXPORTING table  = REF #( lt_stock )
                                                                  programname = 'ZSD_R_STOCK'
                                                                 IMPORTING fieldcatalog = Fieldcatalog
                                                                ).
      "All characteristics in the customization table dynamically added
      ASSIGN Result->* TO FIELD-SYMBOL(<Table>).
