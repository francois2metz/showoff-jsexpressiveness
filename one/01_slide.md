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

    @@@ javascript
    eat food for food in ['toast', 'cheese', 'wine']

!SLIDE

    @@@ javascript
    numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    part = numbers[3..6]

!SLIDE
# Fuyez !

!SLIDE center
# Différents type de code

!SLIDE bullets incremental

* Le mauvais code
* Le bon code

!SLIDE
# Pourquoi être expressif ?

!SLIDE
# Puoqroui êrte esifxserps ?

!SLIDE small

    @@@ javascript
    for (var i = 0; ???
       if (doc.path[i].Education && doc[i].Education.institution.id)
          for (var j = ....
              ...
              emit(doc)
       ...
       ...
    ..

!SLIDE small

    @@@ javascript
    var arr = [
                 {
                     page: 1,
                     src: 'http://exemple.com/img1.jpg',

                 },
                 {
                     page: 2,
                     src: 'http://exemple.com/img2.jpg',

                 },
                 ....
              ]

!SLIDE

    @@@ javascript
    var pages = []
    for (var i = 0; i < arr.length; i++) {
        if (arr[i].page > 3) {
            pages.push(arr[i])
        }
    }

!SLIDE

    @@@ javascript
    var imgs = []
    for (var i = 0; i < pages.length; i++) {
        imgs.push(pages[i].src)
    }

!SLIDE
# underscore.js

## *3kb, Minified and Gzipped*

## http://documentcloud.github.com/underscore/

!uSLIDE

    @@@javaScript
    var imgs = _(arr).chain()
               .filter(function(page) {
                   return (page.page > 3)
               }).map(function(page) {
                   return page.src
               }).value()

!SLIDE bullets incremental

* select
* reduce
* include
* ...

!SLIDE

    @@@javaScript
    _(3).times(fun)

!SLIDE
# Callbacks soup

!SLIDE

    @@@ javascript
    fun1(10, function() {
       fun2(function() {
          fun3(function() {
              fun4(function() {
                 // interesting code here (maybe)
              })
          })
       })
    })

!SLIDE

    @@@javascript
    var sequence = Futures.sequence()
    sequence.then(fun1(10))
            .then(fun2())
            .then(fun3())
            .then(fun4())

!SLIDE

    @@@ javascript
    function callMeAfter(number, fun) {
        var i = 0
        return function() {
           i++
           if (number == i) fun()
        }
    }
    var onEnd = callMeAfter(3, function() {
        alert('finished')
    })
    fun1(onEnd)
    fun2(onEnd)
    fun3(onEnd)

!SLIDE

    @@@javascript
    var join = sequence.join()
    join.add(fun1())
    join.add(fun2())
    join.add(fun3())
    join.when(function() {
       alert('finished')
    })

!SLIDE
# Futures, Promise ..

## https://github.com/coolaj86/futures

## NodeJS && browser

!SLIDE center
# Avertissement
## La fin de cette présentation n'est toujours sur coffee-script

!SLIDE

    @@@javascript
    var ret = fun()
    var a = ret[0]
      , b = ret[1]

!SLIDE

    @@@javascript
    var [a, b] = fun()

!SLIDE small

    @@@javascript
    function plop() {
        var args = Array.prototype.slice.call(arguments, 0)
        args.forEach(function(arg) {
            console.log(arg)
        });
    }

!SLIDE

    @@@javascript
    function plop(...args) {
        args.forEach(function(arg) {
            console.log(arg)
        });
    }

!SLIDE center
# Javascript moderne

## http://code.google.com/p/traceur-compiler/

!SLIDE
# Questions ?
