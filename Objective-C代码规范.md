## 一、命名规范

> 基本原则：见名知意

### 类名

类名（以及类别、协议名）应首字母大写，并以驼峰格式分割单词。

```objective-c
@interface SDAnimatedImage : UIImage <SDAnimatedImage>
```

### 方法名

方法名应该以小写字母开头，并混合驼峰格式。每个具名参数也应该以小写字母开头。

```objective-c
- (void)didReceiveMemoryWarning:(NSNotification *)notification;
```

### 变量名

变量名应该以小写字母开头，并使用驼峰格式

```objective-c
NSData *data;
```

### 常量名

常量名（如宏定义、静态局部变量等）应该以小写字母 `k` 开头，使用驼峰格式分隔单词

```objective-c
#define kScreenWidth [UIScreen mainScreen].bounds.size.width
```



## 二、空格、空行和缩进

### 空格

1. 属性修饰符小括号前后各加一个空格

```objective-c
@property (nonatomic, assign) BOOL bufferMiss; // Good
@property(nonatomic, assign)BOOL bufferMiss; // Bad
```

2. +/-和方法返回值之间加一个空格

```objective-c
- (void)didReceiveMemoryWarning:(NSNotification *)notification; // Good
-(void)didReceiveMemoryWarning:(NSNotification *)notification; // Bad
```

3. 非单目运算符（!、++、--）前后各加一个空格，单目运算符不需要

```objective-c
self.currentFrameIndex == 0 && !self.currentFrame  // Good
self.currentFrameIndex==0&&!self.currentFrame  // Bad
```

4. 如果大括号的开区间`{`位于一行的末尾，则`{`前面需要加一个空格

```objective-c
- (void)startPlaying {} // Good
- (void)startPlaying{} // Bad
```

5. if和switch等条件语句中的条件前后各加一个空格

```objective-c
if (!self.bufferMiss) {} // Good
if(!self.bufferMiss){} // Bad
```

6. 指针`*` 之前加一个空格

```objective-c
NSData *data; // Good
NSData*data; // Not Good
```



### 空行

> 基本原则：1.代码清晰；2.每次不能超过一个空行

1. 方法与方法之间空一行

```objective-c
- (void)handleFrameChange {
}

- (void)handleLoopChnage {
}
```



2. 方法内部，不同处理目的之间可以空一行

3. 不同业务属性之间可以空一行

4. `@` （`@interface`、`@protocol`、`@implementation`、`@end`）上下空一行

```objective-c
// Good
@interface SDAsyncBlockOperation ()

@property (assign, nonatomic, getter = isExecuting) BOOL executing;
@property (assign, nonatomic, getter = isFinished) BOOL finished;
@property (nonatomic, copy, nonnull) SDAsyncBlock executionBlock;

@end

// Not Good
@interface SDAsyncBlockOperation ()
@property (assign, nonatomic, getter = isExecuting) BOOL executing;
@property (assign, nonatomic, getter = isFinished) BOOL finished;
@property (nonatomic, copy, nonnull) SDAsyncBlock executionBlock;
@end
```

> AFN和SDWebImage在Class Extension有区别

5. `.h` 中属性和方法声明之间空一行

```objective-c
// Good
@interface SDDisplayLink : NSObject

@property (readonly, nonatomic) CFTimeInterval duration;

+ (nonnull instancetype)displayLinkWithTarget:(nonnull id)target selector:(nonnull SEL)sel;

@end
  
// Not Good
@interface SDDisplayLink : NSObject

@property (readonly, nonatomic) CFTimeInterval duration;
+ (nonnull instancetype)displayLinkWithTarget:(nonnull id)target selector:(nonnull SEL)sel;

@end
```



### 缩进

按照Xcode默认，缩进4个space。

![Xcode缩进](/Users/zhangyanshen/Library/Application Support/typora-user-images/image-20200619112756616.png)



## 三、注释（建议）

1. `.h` 中属性、方法前面的注释使用`///`，后面加一个空格，然后添加注释内容（`option + command + /`）

```objective-c
/// 这是一个test方法
- (void)test;
```

2. `.m` 中的属性、方法前面的注释使用`//`，后面加一个空格，然后添加注释内容（`command + /`）

```objective-c
// 这是一个test方法
- (void)test;
```

3. 多使用`#pragma mark -` <#注释内容#> 区分方法类型，每一种类型内部使用`#pragma mark <#注释内容#>` 进一步区分

```objective-c
#pragma mark - Life Cycle

// 生命周期相关方法
.....

#pragma mark - Delegate

// 代理方法（先系统，后自定义）
.....

#pragma mark - Event Response
  
// 点击事件等方法
.....
  
#pragma mark - Setters/Getters
  
// setter和getter方法
.....
  
#pragma mark - Private Methods
  
// 私有方法
.....
  
#pragma mark - Public Methods
  
// 公有方法
.....

```





