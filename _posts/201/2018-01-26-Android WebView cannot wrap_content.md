---
title: "Android WebView cannot `wrap_content`"
last_modified_at: 2018-01-26T20:43:06-05:00
categories: 
  - Android
tags:
  - WebView
  - Android
---

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

After meaningless hours of testing and StackOverflowing, I suddenly found that it's all because of the latest(1.0.2) version of `ConstraintLayout`. 
I've tried re-anchor views to another views, but it still won't work.

My humble conlusion is : *Use RelativeLayout* when there are many `View`s need to be arranged.
