[正则表达式模板](http://regexlib.com)

json对象的正则表达式：
    "audit_idea_info['\"]:[\\s]*(?<audit_idea>{[^{}]*(((?'Open'{)[^{}]*)+((?'-Open'})[^{}]*)+)*(?(Open)(?!))})"