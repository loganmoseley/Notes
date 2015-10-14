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
