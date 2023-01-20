# email-testing
version 1.0

email info: https://en.wikipedia.org/wiki/Email_address

| Check                                                                                                        | Data                                                                   | Expected result |
|--------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|-----------------|
| Minimum number of symbols                                                                                    | min                                                                    | ok              |
| Min number of symbols - 1                                                                                    | min - 1                                                                | error message   |
| Min number of symbols + 1                                                                                    | min + 1                                                                | ok              |
| Empty field                                                                                                  |                                                                        | error message   |
| Avr number of symbols (somewhere between min and max)                                                        | avr                                                                    | ok              |
| Maximum number of symbols                                                                                    | max                                                                    | ok              |
| Max number of symbols - 1                                                                                    | max - 1                                                                | ok              |
| Max number of symbols + 1                                                                                    | max + 1                                                                | error message   |
| Space before local-part                                                                                      |  test@test.te                                                          | error message   |
| Space after local-part                                                                                       | test @test.te                                                          | error message   |
| Space in the end                                                                                             | test@test.te                                                           | error message   |
| Space in the middle of local-part                                                                            | tes t@test.te                                                          | error message   |
| Space at the start and end of email                                                                          |  test@test.te                                                          | error message   |
| Enter the email of already registered user                                                                   |                                                                        | error message   |
| Non ANCII symbols                                                                                            | tes¿t@test.te                                                          | error message   |
| Non latin symbols                                                                                            | тест@тест.те                                                           | error message   |
| HTML tags                                                                                                    | <b>test@test.te</b>                                                    | error message   |
| Delete at sign @                                                                                             | testtest.te                                                            | error message   |
| Add another at sign @                                                                                        | test@@test.te                                                          | error message   |
| Add comment to local-part                                                                                    | test.test@(comment)test.te                                             | ok              |
| Add comment to domain                                                                                        | test.test@test.te(comment)                                             | ok              |
| Email with slash                                                                                             | test/test@test.te                                                      | ok              |
| Top level domain e-mail                                                                                      | tes@t.test                                                             | ok              |
| Dotless e-mail                                                                                               | admin@mailserver1                                                      | ok              |
| Valid space in e-mail                                                                                        | " "@test.te                                                            | ok              |
| Invalid double dot in e-mail                                                                                 | te..st@test.te                                                         | error message   |
| Valid double dot in e-mail                                                                                   | "te..st"@test.te                                                       | ok              |
| First dot in local-part                                                                                      | .test@test.te                                                          | error message   |
| Last dot in local-part                                                                                       | test.@test.te                                                          | error message   |
| The exclamation mark (!) (bangified host route used for uucp mailers)                                        | test!test@test.te                                                      | ok              |
| E-mail include non-letters character AND multiple at sign                                                    | "very.(),:;<>[]\".VERY.\"very@\\ \"very\".unusual"@strange.example.com | ok              |
| % escaped mail route to user@example.com via example.org                                                     | user%example.com@example.org                                           | ok              |
| Local part ending with non-alphanumeric character from the list of allowed printable characters              | test-@test.te                                                          | ok              |
| IP addresses are allowed instead of domains when in square brackets, but strongly discouraged                | tester@[123.123.123.123]                                               | ok              |
| IPv6 uses a different syntax                                                                                 | postmaster@[IPv6:2001:0db8:85a3:0000:0000:8a2e:0370:7334]              | ok              |
| None of the special characters in this local-part are allowed outside quotation marks                        | a"b(c)d,e:f;gi[j\k]l@test.te                                           | error message   |
| Quoted strings must be dot separated or the only element making up the local-part                            | test"not"right@test.te                                                 | error message   |
| Spaces, quotes, and backslashes may only exist when within quoted strings and preceded by a backslash        | is"not\allowed@test.te                                                 | error message   |
| Even if escaped (preceded by a backslash), spaces, quotes, and backslashes must still be contained by quotes | this\ still\"not\\allowed@test.te                                      | error message   |
| Underscore is not allowed in domain part                                                                     | test@t_e_s_t.test.te                                                   | error message   |
| Icon characters                                                                                              | QA[icon]CHOCOLATE[icon]@test.te                                        | error message   |
| Emoji ❤️ in local-part                                                                                       | te❤️st@test.te                                                          | error message   |
| Emoji ❤️ in domain                                                                                           | test@te❤️st.te                                                          | error message   |
| Zalgo text e-mail                                                                                            | t̵̢̯̖̪̅̓̇̌e̵̺͚͊̑͐s̷̨̹̿̔͒͝t̵̖͕͕̍̔͠͝@̷̨̭̣̾t̷͕͖̮̳̍e̵͖̣͑͗s̵̛̼̺̎̎̎t̵̡̝̿͐̈́.̴͓͎́́t̶̞͕͂̒́̒e̷̡͍̮͘                                                           | error message   |
| Basic JS                                                                                                     | alert( 'test@test.te' );                                               | error message   |
| Basic XSS                                                                                                    | <body onload=alert('test@test.te')>                                    | error message   |
| SQL injection 1                                                                                              | select title, text from news where id=$id                              | error message   |
| SQL injection 2                                                                                              | “ or 1=1;--                                                            | error message   |
| SQL injection 3                                                                                              | ' or 1=1;--                                                            | error message   |
| SQL injection 4                                                                                              | ‘                                                                      | error message   |
| SQL injection 5                                                                                              | ‘ or ‘abc‘=‘abc‘;--                                                    | error message   |
| SQL injection 6                                                                                              | ‘ or 1=1; drop table users; --                                         | error message   |
| SQL injection 7                                                                                              | "                                                                      | error message   |
| Entering data from the clipboard                                                                             | ???                                                                    | ???             |
| Space in email                                                                                               |                                                                        | error message   |
