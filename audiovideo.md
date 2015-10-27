HTML5 Audio API
===============

Enabling Audio support
----------------------

For security reasons, before the Autotip extension will pickup tips from audio elements using this API, you must first enable Autotip's "Audio Mode". This is done by adding the "Audio Microtip" tag onto the page:

``` html
<meta name="microtip" content="audio">
```

You can use the Audio Microtip tag in conjunction with normal microtip meta tags:

``` html
<meta name="microtip" content="1K65TijR56S4CcwjXBnecYEKmTNrMag5uq">
<meta name="microtip" content="audio">
```

In this case, the first tag tells Autotip how to tip the page creators, and the second microtip tag tells the extension to look for more tips by monitoring the page's audio tags.

Specifying Tip addresses and tip recipients for songs
-----------------------------------------------------

In the body of the document, there will be an audio element where the user can listen to your song. Inside the body of theaudio element, place a JSON encoded list of tips:

``` html
<audio src="http://musicstation.tips.s3.amazonaws.com/08_Free_Four.mp3" controls>
    [{address: "1F4xND22B7qxDtPoGDBLXaxGKXPCyV1c4T"}]
</audio>
```

Note: Even if there is only one tip address (as is the most often case), that tip must be defined as a one element list. Just like with the meta tag speficifation, extra attributes can be defined:

``` html
<audio src="http://musicstation.tips.s3.amazonaws.com/08_Free_Four.mp3" controls>
    [
        {
            address: "1F4xND22B7qxDtPoGDBLXaxGKXPCyV1c4T",
            recipient: "Pink Floyd",
            ratio: 0.75
        },
        {
            address: "1K65TijR56S4CcwjXBnecYEKmTNrMag5uq",
            recipient: "Pink Floyd's Management",
            ratio: 0.25
        }
    ]
</audio>
```

This is technically against the HTML specification, since audio elements are supposed to be "block only" elements. This method was chosen for version 1.0 of this API because of limitations of the chrome extension api.

Actual Example
--------------

The following media element is sourced by the code listed above:

<audio src="http://musicstation.tips.s3.amazonaws.com/08_Free_Four.mp3" controls>
    [{address: "1F4xND22B7qxDtPoGDBLXaxGKXPCyV1c4T", recipient: "Pink Floyd (from the autotip examples page)"}]
</audio>

If you have Autotip installed... You should see the yellow music icon in the address box. Press the play button and hear the music. When the song ends, the chrome extension will pick up the meta tags, and you'll see "Pink Floyd" next to a bitcoin logo in the popup. Click the yellow music icon to see the popup. Inside the popup you'll see a green button. Clicking on that green button will send bitcoin to the recipient.
