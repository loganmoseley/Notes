# Methods

## Collections

Methods returning a collection may return a hydrated collection, an empty collection, or `nil`. Return a hydrated collection when the request was fulfilled. Return an empty collection when the request was fulfilled, but it just so happens nothing was found. Return `nil` when the request does not make sense.

Return `@""` or `nil` from a method that returns NSString?  
A: As with all other collections, return empty if the result of the predicate happens to yield no results, return nil if the input doesn't make sense. Consider `- (NSString *)dweeboidsForName:(NSString *)name` with the examples below:

    NSString *dweeboids = [NYTDweeboids dweeboidsForName:@"Paul"];
    $ po dweeboids >> @[]
    
    NSString *dweeboids = [NYTDweeboids dweeboidsForName:@3];
    $ po dweeboids >> nil

Q: Prefer early returns (`if (_a == a) return;`) or a giant if indentation (`if (_a != a) { ... }`)?  
A: Return early if the input is dirty/invalid/incompatible. For example, an out of bounds error. Use giant if blocks otherwise. Too many giant 'if's? Maybe some refactoring is in order.

## Return A Variable?

Should the intermediate return variable be included? The advantage of A is ease of breakpoints; the advantage of B is succinctness of code.

```
// A
NSURL *applicationSupportDirectoryURL = [URL URLByAppendingPathComponent:bundleIdentifier isDirectory:YES];
return applicationSupportDirectoryURL;

// B
return [URL URLByAppendingPathComponent:bundleIdentifier isDirectory:YES];
```

# Enumerations

Variables representing an enumerated value, e.g., `-[UIDevice userInterfaceIdiom]` should be only be used with a `switch`. This most clearly delineates the possibilities; requires all possibilities to be considered; and will provide compiler warnings in the case that the enumeration gains, loses, or changes a value.