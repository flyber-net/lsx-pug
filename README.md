### [lsx - LiveScript Extension](https://github.com/sakanabiscuit/lsx)

This is Pug/Jade like syntax library for React DOM written on LiveScript

! This plugin is written LiveScript, you need to install LiveScript. LiveScript is a language which compiles to JavaScript.
```Livescript
    { render } = require 'react-dom'
    { createClass, div, a, p } = require 'lsx-pug'

    main = createClass do

        render : ->
            div() do
                a() 'hello'
                p() 'world'

    window.onload = ->

        'app' |> document.createElement |> document.body.appendChild
        render do
            main []
            'app' |> document.querySelector
```
Object Oriented Programming
```Livescript
    { createClass, Component, div, a, p } = require 'lsx-pug'

    main = createClass class Main extends Component

        render : ->
            div() do
                a() 'hello'
                p() 'world'
```
### Installation

Have Node.js installed.
```Bash
    npm i lsx-pug
```
### Usage

1 import plugin 'lsx-pug'.
```Livescript
    { createClass, div, a, p } = require 'lsx-pug'
```
2 create class and bind. (example:Main)

```Livescript
    Main = createClass do

        render : ->
            div() do
                p [] 'hello'
                a [] 'world'
```

3 render.

```Livescript
    { render } = require 'react-dom'
    render do
        Main []
        'app' |> document.querySelector
```

### Function

```Livescript
component

    div() 'hello,world'

    # <div>hello,world</div>
```

null contents component

```Livescript
    div()

    # <div />
```

nest component
```Livescript
    div() do 
        p()
        p() 'hello,world'

    # <div>
    #     <p />
    #     <p>hello,world</p>
    # </div>
```

set props and style, etc..

```Livescript
    div (test-prop : 'test'
         on-click : @test-func 
         style : {height : 200  width : 200} ) 'hello,world'

    # <div test-prop = "test"
    #      onClick = {this.testFunc}
    #      style = {
    #          height:200
    #          width:200
    #      }>
    #     hello,world
    # <div>
```
use component and set prop-types
```Livescript
    { createClass, type, div} = require 'lsx-pug'

    test-component = createClass do

        prop-types =
            test-class : type.string

        get-default-props = ->
            test-class : 'default'

        render : ->
            div(class-name: @props.test-class) @props.children

    Main = createClass do

        render: ->
            div() do
              test-component( test-class: 'test') 'hello,world'
```
