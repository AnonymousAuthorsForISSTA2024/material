# Annotated Data

This repository saves the annotated data for fine-tuning LLMs in the step of rule filtering and rule element extraction.

- The files in **business_rule_documents/** are documents that contain the business rule.
- The *json* files in **annotated_data_for_rule_filtering/** are annotated data for training the rule filtering model. Each item in a file consists of 4 fields: *id* (if has), *text*, *type* and *label*. *id* is the unique primary key for the item. *text* is the rule described in natural language. *type* is the type of text, see Table 1 for more detail. *label* is used for rule element extraction.
- The *json* file in **annotated_data_for_rule_element_extraction** are annotated data for training the extraction model. Each item in a file consists of 3 fields: *id*, *text*, *label*. The annotation adopts the common named entity recognition (NER) format, where each label separated by a space in the *label* is the annotation for each token in the *text*. *B-\** represents the beginning of a label \*, *I-\** is in the middle and end of it, and *O* indicates no label. All the label and their meaning used here are listed in Table 2.

#### Table 1: 
|Type|Description|
|---|---|
|0|Rules that are not testable|
|1|Rules that are testable|
|2|Domain knowledge|

#### Table 2:

|Label|Description|
|---|---|
|O|Unrelated token|
|交易品种|Bond, Stock, Fund, ...|
|交易方式|Matching Trading, Click Trading, ...|
|时间|Constraints on time|
|数量|Constraints on quantity|
|价格|Constraints on price|
|操作人|The person who perform an operation|
|操作|The operation performed by people|
|操作部分|The object of operation|
|结果|Success or Failure|
|key|The label of other tag not listed|
|value|The value of key|
|事件|Precondition or Postcondition of an operation|
|状态|State of the transaction|
|结合规则|Relevant another rule|
|or|Represent the or relation|
|op|key-op-value, such as price greater than 100|
