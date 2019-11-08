### Palavras/frases ou strings

Sempre estarão entre aspas, podendo ser duplas:

```ruby
evento = "Rails Girls"
```

Ou aspas simples:

```ruby
evento = 'Rails Girls'
```

Esse tipo é chamado **String**.

Formas de trabalhar com **Strings**:

```ruby
(irb)> "O resultado e #{5 + 2}"
"O resultado e 7"
(irb)> "Estou no " + evento
# "Estou no Rails Girls"
(irb)> '1' * 5
# 11111
(irb)> 'E!' * 5
# E!E!E!E!E!E!
```

```ruby
(irb)> "casa".include? "asa"  # true
(irb)> "casa".length          # 4
(irb)> "casa".gsub("a","A")   # "cAsA"
(irb)> "  casa  ".rstrip      # "  casa"
(irb)> "casa".count("a")      # 2
(irb)> "2".to_i               # 2
(irb)> 2.to_s                 # "2"
(irb)> "2".to_f               # 2.0
(irb)> "2".rjust(5,"0")       # 00002
```
