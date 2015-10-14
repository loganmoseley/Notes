# Objective-C Lingo

## Method Parameter

### For

Parameter as predicate.

"For" is used in a method signature to express a predicate-style parameter.

```
- (NSArray *)weekdaysForInitialLetter:(NSString *)letter;
$ @"T" >> @[@"Tuesday", @"Thursday"]
```

```
-[NSDictionary objectForKey:]
```

### From

Parameters are necessary and sufficient.

"From" is used in a method signature to express that the parameter or parameters are sufficient to describe the output. The parameters are likely transformed or coerced into other values or presentations, but may not be combined with other information. The parameters are the only changing factors in the method.

```
+ (NSDate *)nextNoonDateFromWeekday:(NSString *)weekday;
$ @"Tuesday" >> 2014-10-21 12:00:00
```

```
NSStringFromCGRect()
```

### With

Parameters are necessary, but not sufficient.

"With" is used in a method signature to express that the parameter or parameters are necessary to the output, but insufficient to fully describe the output. That is, they will be combined with other assumed/implicit information to yield the result.

```
+ (NSString *)favoriteDayTextWithWeekday:(NSString *)weekday;
$ @"Tuesday" >> @"My favorite day is Tuesday!"
```

```
-[NSString uppercaseStringWithLocale:]
```

## Method Signature

### shouldXyz

Expresses a **verb**.

```
- (BOOL)shouldAutomaticallyForwardRotationMethods;
```

### wantsXyz

Expresses a **noun**.

```
- (BOOL)wantsPushNotifications;
```
