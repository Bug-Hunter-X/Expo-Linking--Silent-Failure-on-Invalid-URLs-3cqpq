# Expo Linking Silent Failure on Invalid URLs

This repository demonstrates a subtle bug in Expo's `Linking` API where attempts to open invalid or inaccessible URLs fail silently, providing no clear error message to the developer. This makes debugging difficult and can lead to unexpected behavior in applications.

The `bug.js` file shows how an invalid URL is handled (or rather, mishandled) by the `Linking.openURL` method. The `bugSolution.js` file provides a solution to improve error handling and give more informative feedback.

## Problem:

When `Linking.openURL` is called with an invalid or inaccessible URL, the promise it returns resolves, but without any indication of failure. This makes it challenging for developers to identify the source of the problem.  The lack of a proper error prevents better user experience such as displaying a 'link not found' message.

## Solution:

The solution involves adding robust error handling to wrap the `Linking.openURL` call.  This involves using `.catch` to handle any rejections from the promise and log a meaningful error message, providing more information about why the URL couldn't be opened, leading to better debugging and, consequently, improved app stability.