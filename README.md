Android-Lib-reCAPTCHA
=====================

The reCAPTCHA Android Library provides a simple way to show a <a href="http://www.google.com/recaptcha/captcha">CAPTCHA</a> as an <code>ImageView</code> in your Android app, helping you stop bots from abusing it. The library wraps the <a href="https://developers.google.com/recaptcha/intro">reCAPTCHA API</a>.

To use reCAPTCHA with Android, you can download the <a href="https://github.com/ayltai/Android-Lib-reCAPTCHA/blob/master/reCAPTCHA-Samples/libs/android-lib-recaptcha-0.0.1-SNAPSHOT.jar">reCAPTCHA Android Library here</a>. Typically the only thing you'll need is the jar file (android-lib-recaptcha-x.x.x.jar), which you have to copy to a place where it can be loaded by your IDE. For example, if you are using Eclipse, you can put the jar file in a directory called /libs.

<img src="https://raw.githubusercontent.com/ayltai/Android-Lib-reCAPTCHA/master/screenshot.png" width="422" height="714" alt="Screenshot" />

Quick Start
-----------

After you've <a href="http://www.google.com/recaptcha/whyrecaptcha">signed up for your API keys</a> and downloaded the <a href="https://github.com/ayltai/Android-Lib-reCAPTCHA/blob/master/reCAPTCHA-Samples/libs/android-lib-recaptcha-0.0.1-SNAPSHOT.jar">reCAPTCHA Android Library</a>, below are basic instructions for using <a href="http://www.google.com/recaptcha/captcha">CAPTCHA</a> in your Android application.

**The Layout**

To show CAPTCHA image, you need to add a `<android.lib.recaptcha.ReCaptcha />` element to your layout XML:

<pre>
&lt;android.lib.recaptcha.ReCaptcha
    android:id="@+id/recaptcha"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:scaleType="centerInside" /&gt;
</pre>

It is important to use `android:scaleType="centerInside"` to ensure the entire <a href="http://www.google.com/recaptcha/captcha">CAPTCHA</a> image can be displayed.

Alternatively, you can create an instance of `android.lib.recaptcha.ReCaptcha` at runtime:

<pre>ReCaptcha reCaptcha = new ReCaptcha(context);</pre>

**How to show CAPTCHA**

In your activity/fragment/view containing `android.lib.recaptcha.ReCaptcha`, you need display a <a href="http://www.google.com/recaptcha/captcha">CAPTCHA</a> image for the user to response:

<pre>
ReCaptcha reCaptcha = (ReCaptcha)findViewById(R.id.recaptcha);
reCaptcha.showChallengeAsync("your-public-key", onShowChallengeListener);
</pre>

`showChallengeAsync` downloads and shows <a href="http://www.google.com/recaptcha/captcha">CAPTCHA</a> image asynchronously. It is safe to invoke in UI thread. No exception will be thrown in case of any error by this call. All errors will be treated as unsuccessful in showing <a href="http://www.google.com/recaptcha/captcha">CAPTCHA</a> image.

`onShowChallengeListener` is an instance of `ReCaptcha.OnShowChallengeListener`, which is called when an attempt to show a <a href="http://www.google.com/recaptcha/captcha">CAPTCHA</a> is completed.

The synchronous version of this method is `showChallenge`.

**How to verify user input**

To verify user input, pass the input string to `ReCaptcha.verifyAnswerAsync` (or `ReCaptcha.verifyAnswer`):

<pre>reCaptcha.verifyAnswerAsync("your-private-key", "user-input", onVerifyAnswerListener);</pre>

`verifyAnswerAsync` asynchronously submits the user input string to reCAPTCHA server for verification. It is safe to invoke in UI thread. No exception will be thrown in case of any error by this call. All errors will be treated as verification failure.

`onVerifyAnswerListener` is an instance of `ReCaptcha.OnVerifyAnswerListener`, which is called when an attempt to verify the user input is completed.

The synchronous version of this method is `verifyAnwser`.

Sample Application
------------------

A complete sample application is available at <a href="https://github.com/ayltai/Android-Lib-reCAPTCHA/tree/master/reCAPTCHA-Samples">https://github.com/ayltai/Android-Lib-reCAPTCHA/tree/master/reCAPTCHA-Samples</a>.
