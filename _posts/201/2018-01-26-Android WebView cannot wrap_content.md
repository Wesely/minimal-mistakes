Usually, although not recommended by official, an `WebView` can wrap_content after `loadUrl()` or `loadDataWithBaseUrl()`
by doing this : 
```android
webView.setLayoutParams(
  new LinearLayout.LayoutParams(
    ViewGroup.LayoutParams.MATCH_PARENT,
    ViewGroup.LayoutParams.WRAP_CONTENT
  )
);
```

If this won't work, here's a checklist:
- Don't put `WebView` inside `ScrollView`, use `NestedScrollView` instead.
- Make sure NONE of `WebView`'s parent is using `wrap_content` as `layout_height`.
- Don't use `ConstraintLayout` it seems buggy (to me), `WebView` works fine in `RelativeLayout`

If none of these work, you should try [WrapContentWebView]: https://goo.gl/YGahgx

## My Experence

I had a bunch of `WebView` inside `Vertical LinearLayout` works fine, until I update 
`com.android.support.constraint:constraint-layout` to `1.0.2`. My `WebView` height becomes 0 while using wrap_content.

After many test and survey on StackOverflow, I suddenly found that it's all about the latest version of `ConstraintLayout`. 
I've tried re-anchor views to another views, but it still won't work.

My humble conlusion is : *Use RelativeLayout* when there are many `View`s need to be arranged.
