!SLIDE
# Expressivité du code javascript
## François de Metz
## af83

!SLIDE center
# Avertissement
## Cette présentation n'est pas une présentation sur coffee-script

!SLIDE

    @@@ javascript
    number = -42 if opposite

!SLIDE

    eat food for food in ['toast', 'cheese', 'wine']

!SLIDE center

# Différents type de code

!SLIDE bullets incremental

* Le mauvais code
* Le bon code

!SLIDE

    @@@ javascript
    var result = true;
    for (var i = 0; i < arr.length; i++) {
        if (arr[i].enabled === false) {
            result = false
            break
        }
    }

!SLIDE

    @@@ javascript
    var i = 0
    while (i < 3) {
        i++
        fun()
    }

!SLIDE

    @@@ javascript
    if (arr typeof == 'Array')
        fun()

!SLIDE execute

    @@@javaScript
    var arr = [{enabled: false}, {enabled: true}]
    var result = _(arr).all(function(val) {
        return (val.enabled === true)
    })
    alert(result)

!SLIDE

    @@@javaScript
    _(3).times(fun)

!SLIDE

    @@@javaScript
    if (_([]).isArray())
      fun();

!SLIDE

# Utilisez underscore.js

## *3kb, Minified and Gzipped*

## http://documentcloud.github.com/underscore/

!SLIDE

<iframe src="http://documentcloud.github.com/underscore/" width="100%" height="600px">

!SLIDE

# Callbacks soup

!SLIDE

    @@@ javascript
    fun1(10, function() {
       fun2(function() {
          fun3(function() {
              fun4(function() {
                 // interesting code here
              })
          })
       })
    })

!SLIDE

    @@@ javascript
    var end = function(number, fun) {
        var i = 0
        return function() {
           i++
           if (number == i) fun()
        }
    }
    var onEnd = end(3, function() {
        alert('finished')
    });
    fun('plop', onEnd)
    fun('plip', onEnd)
    fun('cataclop', onEnd)


!SLIDE

    @@@javascript
    var sequence = Futures.sequence()
    sequence.then(fun1)
            .then(fun2)
            .then(fun3)
            .then(fun4)

!SLIDE

    @@@javascript
    var join = sequence.join()
    join.add(fun1)
    join.add(fun2)
    join.add(fun3)
    join.when(function() {
       alert('finished')
    })

!SLIDE

# Futures, Promise ..

## https://github.com/coolaj86/futures

## NodeJS && browser

!SLIDE

    @@@javascript
    var ret = fun()
    var a = ret[0]
      , b = ret[1]

!SLIDE

    @@@javascript
    var [a, b] = fun()

!SLIDE

    @@@javascript
    function plop() {
        arguments = Array.prototype.slice.call(arguments, 0);
        arguments.forEach(function(arg) {
            console.log(arg);
        });
    }

!SLIDE

    @@@javascript
    function plop(...args) {
        args.forEach(function(arg) {
            console.log(arg);
        });
    }

!SLIDE center

# Utiliser du javascript moderne

## http://code.google.com/p/traceur-compiler/

!SLIDE

# Questions ?
