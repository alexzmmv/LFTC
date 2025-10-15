// Whitespace and comments may appear between any tokens and are ignored.

<program> ::= <statement_list>

<statement_list> ::= <statement> | <statement> <statement_list>

<statement> ::= <matched_statement> | <unmatched_statement>

<matched_statement> ::= <simple_statement>
                     | "if" "(" <expression> ")" "{" <matched_statement> "}" "else" "{" <matched_statement> "}"

<unmatched_statement> ::= "if" "(" <expression> ")" "{" <statement> "}"
                       | "if" "(" <expression> ")" "{" <matched_statement> "}" "else" "{" <unmatched_statement> "}"

<simple_statement> ::= <assignment> ";" 
                    | <for_statement> 
                    | <iterate_statement> 
                    | <print_statement> ";"
                    | <input_statement> ";"

<assignment> ::= <identifier> "=" <expression>

<for_statement> ::= "for" "(" <assignment> ";" <expression> ";" <assignment> ")" "{" <statement_list> "}"

<iterate_statement> ::= "iterate" "(" <identifier> "in" <list> ")" "{" <statement_list> "}"

<print_statement> ::= "put" "(" <expression> ")"

<input_statement> ::= <input_source> ">>" <identifier>

<input_source> ::= "terminal"

<expression> ::= <logical_or_expr> [ "?" <expression> ":" <expression> ]

<logical_or_expr> ::= <logical_and_expr> { ("or") <logical_and_expr> }

<logical_and_expr> ::= <logical_not_expr> { ("and") <logical_not_expr> }

<logical_not_expr> ::= [ "not" | "!" ] <comparison>

<comparison> ::= <term> { <comparator> <term> }

<term> ::= <factor> { ("+" | "-") <factor> }

<factor> ::= <primary> { ("*" | "/") <primary> }

<primary> ::= <base_primary> { "[" <expression> "]" }

<base_primary> ::= <identifier>
                | <constant>
                | <list>
                | <nill>
                | "(" <expression> ")"

<list> ::= "[" [ <list_elements> ] "]"

<list_elements> ::= <expression> | <expression> "," <list_elements>

<constant> ::= <number> | <string_literal> | <character>

<identifier> ::= <letter> { <letter> | <digit> }

<string_literal> ::= "\"" { <character> } "\""

<character> ::= <letter> | <digit> | <special_char>

<special_char> ::= "!" | "*" | "(" | ")" | "-" | "_" | "+" | "=" | "{" | "}" 
                 | "[" | "]" | "|" | "\\" | ":" | ";" | "'" | "<" | ">" 
                 | "," | "." | "?" | "/" | " " 

<comparator> ::= "==" | "===" | "!=" | "!==" | "<" | ">" | "<=" | ">="

<number> ::= <digit> { <digit> }

<nill> ::= "nill"

<letter> ::= "a" | "b" | ... | "z" | "A" | "B" | ... | "Z"

<digit> ::= "0" | "1" | ... | "9"

<whitespace> ::= " " | "\t" | "\n"

<comments> ::= <single_line_comment> | <multi_line_comment>

<single_line_comment> ::= "!!" { <uppercase_letter> | <whitespace> | <special_char> | <digit> } <newline>
<multi_line_comment> ::= "!!!" { <uppercase_letter> | <whitespace> | <special_char> | <digit> | <newline> } "!!!"

<uppercase_letter> ::= "A" | "B" | ... | "Z"
<newline> ::= "\n"

<separators> ::= ";" | "," | "(" | ")" | "{" | "}" | "[" | "]"

<operators> ::= "+" | "-" | "*" | "/" | "=" 
              | "==" | "===" | "!=" | "!==" 
              | "<" | ">" | "<=" | ">=" 
              | "!" | "?" | ":"

<reserved_keywords> ::= "if" | "else" | "for" | "iterate" | "in" | "nill" | "put" 
                      | "and" | "or" | "not" | "terminal"

(* Whitespace and comments may appear between any tokens and are ignored. *)
//modify for matrices operations