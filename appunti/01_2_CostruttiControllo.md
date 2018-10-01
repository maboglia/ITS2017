# Costrutti di controllo

Costrutti di controllo di flusso delle istruzioni

Il controllo dell'esecuzione di istruzioni vene gestito da costrutti molto simili a quelli di
Java.

Si rimanda al manuale php http://www.php.net/manual/en/language.control-structures.php
per gli approfondimenti

## Sequenza
Elenco di istruzioni fra parentesi graffe
```{ <statement> ... <statement> }```

## Alternativa

Scelta fra due o più vie alternative (una sì e le altre no)
```php
if
if (<espressione>) <statement>
if ... else
if (<espressione>) <statement>
else <statement>
else if
if (<espressione>) <statement>
elseif (<espressione>) <statement>
...
elseif (<espressione>) <statement>
else <statement>
```

## switch
Ha una sintassi articolata, esemplifico qui il caso più ricorrente:

```php 
switch (<espressione>){
case <valore1>:
<statement>...<statement>
break;
case <valore2>:
<statement>...<statement>
break;
... altri case ...
case <valoreN>:
<statement>...<statement>
break;
default:
<statement>...<statement>
break;
}
```

La presenza del break non è vincolo sintattico, la sua assenza comporterebbe che
terminata l'esenzione delle istruzioni di un caso verrebbero eseguite anche le seguenti

## Iterazione
Costrutti per la esecuzione ripetuta di istruzioni

## while
```
while (<espressione>) <statement>
```

## do while
```do <statement> while (<espressione>)```

## for
```for (<espressione1>;<espressione2>;<espressione3>) <statement>```

## foreach

sintassi 1
```foreach (<array_expression> as <variabile>) <statement>```
sintassi 2
```foreach (<array_expression> as <variabileK> => <variabileV>)<statement>```

## break

Interrompe l'esecuzione del costrutto in cui è inserito, tipica applicazione è all'interno dello
switch come visto in precedenza. Può essere utilizzato anch all'interno di for, foreach,
while, do-while, in tal caso interrrompe forzatamente la ripetizione.

## continue

Salta cioè che segue all'interno del costrutto ciclico in cui è inserito, senza però
interrompere necessariamentre la ripetizione

## return
```return <espressione>```

Interrompe l'esecuzione del metodo corrente e restituisce all'ambiente chiamante il valore
ottenuto valutando l'espressione.


## Istruzioni if

Nell’utilizzo di istruzioni ‘if/else’ in una funzione o in una classe, si pensa spesso che ‘else’ debba essere necessariamente usato per potenziali risultati. Ma se il risultato è la restituzione di un valore, ‘else’ non è necessario, perché ‘return’ terminerà la funzione, rendendo ‘else’ inutile.
```php
    <?php
    function test($a)
    {
        if ($a) {
            return true;
        } else {
            return false;
        }
    }
    
    // contro
    
    function test($a)
    {
        if ($a) {
            return true;
        }
        return false;    // else non è necessario
    }

*   [Costrutti if](http://php.net/control-structures.if)
```

## Istruzioni switch

Le istruzioni switch sono un ottimo modo per evitare di scrivere infiniti if ed elseif, ma ci sono un paio di cose a cui prestare attenzione:

*   Le istruzioni switch confrontano solo i valori, non il tipo (equivalente a ‘==’)
*   Iterano caso dopo caso finché non viene trovata una corrispondenza. Se non viene trovata, viene eseguita quella di default (se definita)
*   Senza un ‘break’, continueranno a implementare ogni caso finché non raggiungono un break/return
*   In una funzione, l’utilizzo di ‘return’ elimina la necessità per un ‘break’, perché esso termina la funzione

```php
    <?php
    $answer = test(2);    // sia il codice del 'case 2', sia quello del 'case 3' saranno implementati
    
    function test($a)
    {
        switch ($a) {
            case 1:
                // codice...
                break;             // break viene usato per terminare l'istruzione switch
            case 2:
                // codice...         // senza un break, il confronto continua fino al caso 3
            case 3:
                // codice...
                return $result;    // in una funzione, 'return' termina la funzione
            default:
                // codice...
                return $error;
        }
    }
```

*   [Istruzioni switch](http://php.net/control-structures.switch)
*   [PHP switch](http://phpswitch.com/)






Quest'opera è stata rilasciata con licenza Creative Commons Attribuzione - Non commerciale - Condividi allo stesso modo 3.0 Italia. Per leggere una
copia della licenza visita il sito web http://creativecommons.org/licenses/by-nc-sa/3.0/it/ o spedisci una lettera a Creative Commons, 171 Second
Street, Suite 300, San Francisco, California, 94105, USA.
Giovanni Ragno – ITIS Belluzzi Bologna 2011