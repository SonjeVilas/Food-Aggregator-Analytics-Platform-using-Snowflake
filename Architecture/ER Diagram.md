# Food Aggregator — ER Diagram (CONSUMPTION_SCH Star Schema)

Central fact `ORDER_ITEM_FACT` (grain: one row per order item) linked to 7 SCD-style
dimensions via surrogate hash keys (`*_HK`).

```mermaid
erDiagram
    ORDER_ITEM_FACT }o--|| CUSTOMER_DIM             : CUSTOMER_DIM_KEY
    ORDER_ITEM_FACT }o--|| CUSTOMER_ADDRESS_DIM     : CUSTOMER_ADDRESS_DIM_KEY
    ORDER_ITEM_FACT }o--|| RESTAURANT_DIM           : RESTAURANT_DIM_KEY
    ORDER_ITEM_FACT }o--|| RESTAURANT_LOCATION_DIM  : RESTAURANT_LOCATION_DIM_KEY
    ORDER_ITEM_FACT }o--|| MENU_DIM                 : MENU_DIM_KEY
    ORDER_ITEM_FACT }o--|| DELIVERY_AGENT_DIM       : DELIVERY_AGENT_DIM_KEY
    ORDER_ITEM_FACT }o--|| DATE_DIM                 : ORDER_DATE_DIM_KEY

    ORDER_ITEM_FACT {
        number ORDER_ITEM_FACT_SK PK
        number ORDER_ITEM_ID
        number ORDER_ID
        number CUSTOMER_DIM_KEY FK
        number CUSTOMER_ADDRESS_DIM_KEY FK
        number RESTAURANT_DIM_KEY FK
        number RESTAURANT_LOCATION_DIM_KEY FK
        number MENU_DIM_KEY FK
        number DELIVERY_AGENT_DIM_KEY FK
        number ORDER_DATE_DIM_KEY FK
        number QUANTITY
        number PRICE
        number SUBTOTAL
        text DELIVERY_STATUS
        text ESTIMATED_TIME
    }

    CUSTOMER_DIM {
        number CUSTOMER_HK PK
        text CUSTOMER_ID
        text NAME
        text MOBILE
        text EMAIL
        text LOGIN_BY_USING
        text GENDER
        date DOB
        date ANNIVERSARY
        text PREFERENCES
        timestamp EFF_START_DATE
        timestamp EFF_END_DATE
        boolean IS_CURRENT
    }

    CUSTOMER_ADDRESS_DIM {
        number CUSTOMER_ADDRESS_HK PK
        number ADDRESS_ID
        text CUSTOMER_ID_FK
        text FLAT_NO
        text HOUSE_NO
        text FLOOR
        text BUILDING
        text LANDMARK
        text LOCALITY
        text CITY
        text STATE
        text PINCODE
        text COORDINATES
        text PRIMARY_FLAG
        text ADDRESS_TYPE
        timestamp EFF_START_DATE
        timestamp EFF_END_DATE
        boolean IS_CURRENT
    }

    DATE_DIM {
        number DATE_DIM_HK PK
        date CALENDAR_DATE
        number YEAR
        number QUARTER
        number MONTH
        number WEEK
        number DAY_OF_YEAR
        number DAY_OF_WEEK
        number DAY_OF_THE_MONTH
        text DAY_NAME
    }

    DELIVERY_AGENT_DIM {
        number DELIVERY_AGENT_HK PK
        number DELIVERY_AGENT_ID
        text NAME
        text PHONE
        text VEHICLE_TYPE
        number LOCATION_ID_FK
        text STATUS
        text GENDER
        number RATING
        timestamp EFF_START_DATE
        timestamp EFF_END_DATE
        boolean IS_CURRENT
    }

    MENU_DIM {
        number MENU_DIM_HK PK
        number MENU_ID
        number RESTAURANT_ID_FK
        text ITEM_NAME
        text DESCRIPTION
        number PRICE
        text CATEGORY
        boolean AVAILABILITY
        text ITEM_TYPE
        timestamp EFF_START_DATE
        timestamp EFF_END_DATE
        boolean IS_CURRENT
    }

    RESTAURANT_DIM {
        number RESTAURANT_HK PK
        number RESTAURANT_ID
        text NAME
        text CUISINE_TYPE
        number PRICING_FOR_TWO
        text RESTAURANT_PHONE
        text OPERATING_HOURS
        number LOCATION_ID_FK
        text ACTIVE_FLAG
        text OPEN_STATUS
        text LOCALITY
        text RESTAURANT_ADDRESS
        number LATITUDE
        number LONGITUDE
        timestamp EFF_START_DATE
        timestamp EFF_END_DATE
        boolean IS_CURRENT
    }

    RESTAURANT_LOCATION_DIM {
        number RESTAURANT_LOCATION_HK PK
        number LOCATION_ID
        text CITY
        text STATE
        text STATE_CODE
        boolean IS_UNION_TERRITORY
        boolean CAPITAL_CITY_FLAG
        text CITY_TIER
        text ZIP_CODE
        text ACTIVE_FLAG
        timestamp EFF_START_DT
        timestamp EFF_END_DT
        boolean CURRENT_FLAG
    }
```

## Relationships

| Fact FK column                | References dimension        | On (hash key)             |
|-------------------------------|-----------------------------|---------------------------|
| CUSTOMER_DIM_KEY              | CUSTOMER_DIM                | CUSTOMER_HK               |
| CUSTOMER_ADDRESS_DIM_KEY      | CUSTOMER_ADDRESS_DIM        | CUSTOMER_ADDRESS_HK       |
| RESTAURANT_DIM_KEY           | RESTAURANT_DIM              | RESTAURANT_HK             |
| RESTAURANT_LOCATION_DIM_KEY  | RESTAURANT_LOCATION_DIM     | RESTAURANT_LOCATION_HK    |
| MENU_DIM_KEY                 | MENU_DIM                    | MENU_DIM_HK               |
| DELIVERY_AGENT_DIM_KEY       | DELIVERY_AGENT_DIM          | DELIVERY_AGENT_HK         |
| ORDER_DATE_DIM_KEY           | DATE_DIM                    | DATE_DIM_HK               |

Notes:
- Dimensions are SCD-tracked (`EFF_START/END`, `IS_CURRENT` / `CURRENT_FLAG`).
- FK constraints in Snowflake are informational (not enforced).
