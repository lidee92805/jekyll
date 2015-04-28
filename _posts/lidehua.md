
在适配64位的时候,程序会在objc_msgSend处崩溃,根据苹果的官方文档需要转换<br/>
<pre><code>- (int) doSomething:(int) x { ... }
- (void) doSomethingElse {
    int (*action)(id, SEL, int) = (int (*)(id, SEL, int)) objc_msgSend;
    action(self, @selector(doSomething:), 0);
}
</code></pre>
[苹果官方文档地址](https://developer.apple.com/library/ios/documentation/General/Conceptual/CocoaTouch64BitGuide/ConvertingYourAppto64-Bit/ConvertingYourAppto64-Bit.html)
