## Schnittstelle

#### Installation

> pip install schnittstelle

##### Import

```python

# completer
from schnittstelle import Completer, CompleterStyle, RunnableCompleter

# loader
from schnittstelle import Loader, LoaderStyle, RunnableLoader

# decorators
from schnittstelle import decorators

```

#### [**Completer**](https://github.com/mHaisham/schnittstelle/blob/master/schnittstelle/completer/__init__.py)

```
[✓] complete
[X] fail
```

While completer is drawing to `print` use
```python
completer.print('string to print')
```

* #### Use

    ##### `with` statement
       
    > Recommended
       
    ```python
      with Completer('Dummy') as completer:
        # code
        pass
    ```
  
    The object will auto complete when on exiting `with` statement
    
    You may also exit using `completer.complete()` or `completer.fail()`
    
    ##### Decorator
    
    ```python
    from schnittstelle import decorators
    
    @decorators.Completer('foo bar')
    def foo(s):
        # code
    ``` 
    
    Everytime the function is called Completer will appear
    
    In case of exception it is caught and runs the fail method of completer
    
    Using this method you're not able to access completer class itself
    
    ##### Inline
    
    ```python
    completer = Completer('').init()

    # code
    
    completer.complete() # or completer.fail()
    ```   
    
    Exit the completer using `completer.complete()` or `completer.fail()`
    
    ##### Runnable
       
    > Not recommended
       
    ```python
    def foo(s):
      # code
    
    runnable = RunnableCompleter(foo, message='foo bar')
    runnable.run('foo')
    ```
  
    All arguments go into run method
    
    In case of exception it is caught and runs the fail method of completer
    
    Using this method you're not able to access completer class itself
    
* #### Configuration

    * [**style**](https://github.com/mHaisham/schnittstelle/blob/master/schnittstelle/loader/style.py)
        
        Takes in class [CompleterStyle](https://github.com/mHaisham/schnittstelle/blob/master/schnittstelle/loader/style.py)
        
        ##### CompleterStyle
        
        ###### _Static Constuctors_
        
        **`default`** default settings
        
        ###### _Attributes_
        
        **`prefix`**
        
        character before char
        
        default: [
        
        **`postfix`**
        
        character after char
        
        default: ]
        
        **`success`**
        
        color of character when successful
        
        default: GREEN
        
        **`error`**
        
        color of character when unsuccessful
        
        default: RED
        
        **`info`**
        
        color of character in info messages
        
        default: BLUE
        
    


#### [**Loader**](https://github.com/mHaisham/schnittstelle/blob/master/schnittstelle/loader/)
    
This is the `progress bar` class of package

```
[==   ] Dummy bar
```

While the progress bar is in progress to `print` use
```python
loader.print('string to print')
```

* #### Use
    
    ##### `with` statement
       
    > Recommended
       
    ```python
      with Loader(message='Dummy bar') as loader:
        # code
        pass
    ```
  
    The bar will auto complete when on exiting `with` statement
    
    You may also exit using `loader.complete()` or `loader.fail()`
    
    ##### Decorator
    
    ```python
    from schnittstelle import decorators
    
    @decorators.Loader(message='foo bar')
    def foo(s):
        # code
    ``` 
    
    Everytime the function is called loader will appear
    
    In case of exception it is caught and runs the fail method of loader
    
    Using this method you're not able to access loader class itself
    
    ##### Inline
    
    ```python
    loader = Loader().init()

    # code
    
    loader.complete() # or loader.fail()
    ```   
    
    Exit the progress bar using `loader.complete()` or `loader.fail()`
    
    ##### Runnable
       
    > Not recommended
       
    ```python
    def foo(s):
      # code
    
    runnable = RunnableLoader(foo, message='foo bar')
    runnable.run('foo')
    ```
  
    All arguments go into run method
    
    In case of exception it is caught and runs the fail method of loader
    
    Using this method you're not able to access loader class itself
    
* #### Configurations
    
    To change the configurations at runtime use `loader.brush.[configuration]` syntax
    
    _configurations need to be passed into class initiator as keyword arguments_

    * ***value***
    
        Current value of progress
        
        If this value is less than 0, the progress bar is `indeterminate`
    
    * ***total***
        
        Total progress for the bar
    
    * ***message***
        
        Message label to display on progress bar
        
        In the above example it is **Dummy bar**
    
    * ***frequency***
        
        Number of refreshes per second
        
        This will determine the `speed` of the progress bar as well
        
        If frequency is too low, progress bar might not show progress as intended
        
        `default` is 20 refreshes per sec
    
    * [**style**](https://github.com/mHaisham/schnittstelle/blob/master/schnittstelle/loader/style.py)
    
        Takes in class [LoaderStyle](https://github.com/mHaisham/schnittstelle/blob/master/schnittstelle/loader/style.py)
        
        ##### LoaderStyle
        
        ###### _Static Constuctors_
        
        **`default`** default settings
        
        **`ascii`** only containing ascii chars
        
        ###### _Attributes_
        
        **`width`** 
        
        width of the progress bar
        
        default: 5
        
        **`cursor_width`**
           
        Fill width of indeterminate progress bar
           
        default: 3
           
        **`fill`**
           
        Fill indicator charactor
        
        default: FULL_BLOCK
           
        **`empty`**
        
        empty indicator charactor
        
        default: SPACE
        
        **`prefix`**
        
        character before progress bar
        
        default: [
        
        **`postfix`**
        
        character after progress bar
        
        default: ]
        
