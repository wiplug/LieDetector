LieDetector
===========

Predicting veracity of broadcast speeches and campaign promises in realtime

<img src="https://raw.github.com/msjoinder/LieDetector/master/layout.jpg">

## What is it for?

Ever like what a politician says on the campaign trail? Of course you have.

Did you wonder if he or she was lying to you? Of course you did.

What if you could analyze the transcript of a politician's speech in realtime?

## Realtime hardware device

LieDetector is an open hardware device to test politicians' statements on TV in realtime against a truth model.

1. Get an Arduino Uno
2. Get the <a href="http://nootropicdesign.com/ve/">Video Experimenter Shield</a> to collect closed-captioning text
3. Connect a purple "lie detector" light to digital pin 6
4. Connect a binary "two-party system" switch to digital pin 13

**If you see a third party candidate speaking on TV, you'll have to modify the device!** I.E. you won't have to modify the device!

Smaller, in-the-field devices could be developed using a speech-to-text device such as
<a href="http://www.bitsophia.com/BitVoicer.aspx">BitVoicer</a>.

## How does the prediction happen?

The
<a href="https://developers.google.com/prediction/">Google Prediction API</a>
is used to develop a computational model of unreliable words and phrases, similar
to how Gmail detects spam messages. You can then feed new sentences into the model
and get a probability that they are TRUE, MISLEADING, or FALSE.

## Building a truth model

Populate statements.csv with a spreadsheet with three columns of known statements:

    TRUE/MISLEADING/FALSE , "USA-DEM"/"USA-REP" , "Text of a statement"
    TRUE, "USA-DEM", "We choose to go to the moon. We choose to go to the moon in this decade and do the other things, not because they are easy, but because they are hard, because that goal will serve to organize and measure the best of our energies and skills, because that challenge is one that we are willing to accept, one we are unwilling to postpone, and one which we intend to win, and the others, too."

Follow directions in the
<a href="https://developers.google.com/prediction/docs/getting-started">Getting Started section</a>
of the Google Prediction API:

* Create a Google Account and a project on <a href="https://cloud.google.com/console">Google Cloud Console</a>

* In the API Console, enable billing, Google Cloud Storage, the Google Cloud Storage JSON API, and the Google Prediction API.

Follow directions in the
<a href="https://developers.google.com/prediction/docs/hello_world">Hello World section</a>
of the Google Prediction API:

* Upload statements.csv to a new bucket in Google Cloud Storage

* Open the API Explorer and train a new prediction model

--
All words and original code licensed under GPLv3
--
