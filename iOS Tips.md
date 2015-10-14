# Implementing a Container View Controller

https://developer.apple.com/library/ios/documentation/uikit/reference/UIViewController_Class/Reference/Reference.html

> Your container view controller must associate a child view controller with itself before adding the child’s root view to the view hierarchy.

```
/* ADD */
[self addChildViewController:childVC];
[self.view addSubview:childViewController.view];
// 1. possible transition logic
[childVC didMoveToParentViewController:self];

/* REMOVE */
[childVC willMoveToParentViewController:nil];
// 2. possible transition logic
[childVC.view removeFromSuperview];
[childVC removeFromParentViewController:nil];
```

### Custom Transitions

Return NO from `shouldAutomaticallyForwardAppearanceMethods` before invoking both these methods at both points (1) or (2) above:

```
[childVC beginAppearanceTransition:isAppearing animated:animated];
[childVC endAppearanceTransition];
```

# Vocabulary

In method naming, "From:" means the method will return a new object derived exclusively from and essentially only describing this parameter, "With:" means the parameter represent a key piece–but not the only piece–of information, and "For:" means the method will return an object or value from existing information (aka, a predicate).

Examples:

* `NSStringFromCGRect()` returns a new NSString based on nothing and representing nothing except for the CGRect
* `-uppercaseStringWithLocale:` returns a new NSString based on the locale passed, but also the existing NSString
* `+stringEncodingForData:encodingOptions:::` returns an NSStringEncoding that matches the given parameters
