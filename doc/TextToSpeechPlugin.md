<!-- Generated automatically, DO NOT EDIT! -->
<a name="head.TextToSpeech_Plugin"></a>
# TextToSpeech Plugin

**Version: 1.0**

**Status: :black_circle::black_circle::black_circle:**

TextToSpeech plugin for Thunder framework.

### Table of Contents

- [Introduction](#head.Introduction)
- [Description](#head.Description)
- [Configuration](#head.Configuration)
- [Methods](#head.Methods)
- [Notifications](#head.Notifications)

<a name="head.Introduction"></a>
# Introduction

<a name="head.Scope"></a>
## Scope

This document describes purpose and functionality of the TextToSpeech plugin. It includes detailed specification of its configuration, methods provided and notifications sent.

<a name="head.Case_Sensitivity"></a>
## Case Sensitivity

All identifiers on the interface described in this document are case-sensitive. Thus, unless stated otherwise, all keywords, entities, properties, relations and actions should be treated as such.

<a name="head.Acronyms,_Abbreviations_and_Terms"></a>
## Acronyms, Abbreviations and Terms

The table below provides and overview of acronyms used in this document and their definitions.

| Acronym | Description |
| :-------- | :-------- |
| <a name="acronym.API">API</a> | Application Programming Interface |
| <a name="acronym.HTTP">HTTP</a> | Hypertext Transfer Protocol |
| <a name="acronym.JSON">JSON</a> | JavaScript Object Notation; a data interchange format |
| <a name="acronym.JSON-RPC">JSON-RPC</a> | A remote procedure call protocol encoded in JSON |

The table below provides and overview of terms and abbreviations used in this document and their definitions.

| Term | Description |
| :-------- | :-------- |
| <a name="term.callsign">callsign</a> | The name given to an instance of a plugin. One plugin can be instantiated multiple times, but each instance the instance name, callsign, must be unique. |

<a name="head.References"></a>
## References

| Ref ID | Description |
| :-------- | :-------- |
| <a name="ref.HTTP">[HTTP](http://www.w3.org/Protocols)</a> | HTTP specification |
| <a name="ref.JSON-RPC">[JSON-RPC](https://www.jsonrpc.org/specification)</a> | JSON-RPC 2.0 specification |
| <a name="ref.JSON">[JSON](http://www.json.org/)</a> | JSON specification |
| <a name="ref.Thunder">[Thunder](https://github.com/WebPlatformForEmbedded/Thunder/blob/master/doc/WPE%20-%20API%20-%20WPEFramework.docx)</a> | Thunder API Reference |

<a name="head.Description"></a>
# Description

The TextToSpeech plugin provides TextToSpeech functionality for Voice Guidance and Speech Synthesis usecases.

The plugin is designed to be loaded and executed within the Thunder framework. For more information about the framework refer to [[Thunder](#ref.Thunder)].

<a name="head.Configuration"></a>
# Configuration

The table below lists configuration options of the plugin.

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| callsign | string | Plugin instance name (default: *org.rdk.TextToSpeech*) |
| classname | string | Class name: *TextToSpeech* |
| locator | string | Library name: *libWPEFrameworkTextToSpeech.so* |
| autostart | boolean | Determines if the plugin is to be started automatically along with the framework |

<a name="head.Methods"></a>
# Methods

The following methods are provided by the TextToSpeech plugin:

TextToSpeech interface methods:

| Method | Description |
| :-------- | :-------- |
| [enableTTS](#method.enableTTS) | Enable TTS Engine |
| [listVoices](#method.listVoices) | To list the supported voice |
| [setTTSConfiguration](#method.setTTSConfiguration) | To set the TTS Configuration |
| [getTTSConfiguration](#method.getTTSConfiguration) | To get the TTS Configuration |
| [isTTSEnabled](#method.isTTSEnabled) | Check whether TTS is enabled or not |
| [isSessionActiveForApp](#method.isSessionActiveForApp) | Check whether TTSSession is active for app or not |
| [acquireResource](#method.acquireResource) | Acquire TTS Resource for app |
| [claimResource](#method.claimResource) | Claim TTS Resource for app |
| [releaseResource](#method.releaseResource) | Release TTS Resource |
| [createSession](#method.createSession) | Create TTS Session |
| [destroySession](#method.destroySession) | Destroy TTS Session |
| [isActiveSession](#method.isActiveSession) | Check whether TTSSession is active or not |
| [setPreemptiveSpeak](#method.setPreemptiveSpeak) | SetPreemptiveSpeak or queeing speech |
| [requestExtendedEvents](#method.requestExtendedEvents) | Set requestExtendedEvents |
| [speak](#method.speak) | Start Speech |
| [abort](#method.abort) | Abort the speech |
| [pause](#method.pause) | Pause the speech |
| [resume](#method.resume) | Resume the speech |
| [isSpeaking](#method.isSpeaking) | Check the session is speaking or not |
| [getSpeechState](#method.getSpeechState) | Get the speech state |

<a name="method.enableTTS"></a>
## *enableTTS <sup>method</sup>*

Enable TTS Engine.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.enableTTS | boolean | Indicates whether TTS Engine to be enable or disable |

### Result

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| result | object |  |
| result?.TTS_Status | number | <sup>*(optional)*</sup> TTS Return status (must be one of the following: *TTS_OK*, *TTS_FAIL*, *TTS_NOT_ENABLED*, *TTS_CREATE_SESSION_DUPLICATE*, *TTS_EMPTY_APPID_INPUT*, *TTS_RESOURCE_BUSY*, *TTS_NO_SESSION_FOUND*, *TTS_NESTED_CLAIM_REQUEST*, *TTS_INVALID_CONFIGURATION*, *TTS_SESSION_NOT_ACTIVE*, *TTS_APP_NOT_FOUND*, *TTS_POLICY_VIOLATION*, *TTS_OBJECT_DESTROYED*, *TTS_SPEECH_NOT_FOUND*) |
| result?.success | boolean | <sup>*(optional)*</sup> Call status |

### Example

#### Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "TextToSpeech.1.enableTTS",
    "params": {
        "enableTTS": true
    }
}
```
#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": {
        "TTS_Status": 0,
        "success": true
    }
}
```
<a name="method.listVoices"></a>
## *listVoices <sup>method</sup>*

To list the supported voice.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.language | string | Specify the language to get the corresponding voice |

### Result

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| result | object |  |
| result?.voices | array | <sup>*(optional)*</sup>  |
| result?.voices[#] | string | <sup>*(optional)*</sup> Supported voice |
| result?.TTS_Status | number | <sup>*(optional)*</sup> TTS Return status (must be one of the following: *TTS_OK*, *TTS_FAIL*, *TTS_NOT_ENABLED*, *TTS_CREATE_SESSION_DUPLICATE*, *TTS_EMPTY_APPID_INPUT*, *TTS_RESOURCE_BUSY*, *TTS_NO_SESSION_FOUND*, *TTS_NESTED_CLAIM_REQUEST*, *TTS_INVALID_CONFIGURATION*, *TTS_SESSION_NOT_ACTIVE*, *TTS_APP_NOT_FOUND*, *TTS_POLICY_VIOLATION*, *TTS_OBJECT_DESTROYED*, *TTS_SPEECH_NOT_FOUND*) |
| result?.success | boolean | <sup>*(optional)*</sup> Call status |

### Example

#### Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "TextToSpeech.1.listVoices",
    "params": {
        "language": "en-US"
    }
}
```
#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": {
        "voices": [
            "carol"
        ],
        "TTS_Status": 0,
        "success": true
    }
}
```
<a name="method.setTTSConfiguration"></a>
## *setTTSConfiguration <sup>method</sup>*

To set the TTS Configuration.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params?.ttsEndPoint | string | <sup>*(optional)*</sup> Specify the ttsEndPoint for TTSEngine |
| params?.ttsEndPointSecured | string | <sup>*(optional)*</sup> Specify the ttsEndPointSecured for TTSEngine |
| params?.language | string | <sup>*(optional)*</sup> Specify the language for TTSEngine |
| params?.voice | string | <sup>*(optional)*</sup> Specify the voice for TTSEngine |
| params?.volume | string | <sup>*(optional)*</sup> Specify the volume for TTSEngine |
| params?.rate | number | <sup>*(optional)*</sup> Specify the rate for TTSEngine |

### Result

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| result | object |  |
| result?.TTS_Status | number | <sup>*(optional)*</sup> TTS Return status (must be one of the following: *TTS_OK*, *TTS_FAIL*, *TTS_NOT_ENABLED*, *TTS_CREATE_SESSION_DUPLICATE*, *TTS_EMPTY_APPID_INPUT*, *TTS_RESOURCE_BUSY*, *TTS_NO_SESSION_FOUND*, *TTS_NESTED_CLAIM_REQUEST*, *TTS_INVALID_CONFIGURATION*, *TTS_SESSION_NOT_ACTIVE*, *TTS_APP_NOT_FOUND*, *TTS_POLICY_VIOLATION*, *TTS_OBJECT_DESTROYED*, *TTS_SPEECH_NOT_FOUND*) |
| result?.success | boolean | <sup>*(optional)*</sup> Call status |

### Example

#### Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "TextToSpeech.1.setTTSConfiguration",
    "params": {
        "ttsEndPoint": "http://ccr.voice-guidance-tts.xcr.comcast.net/tts/v1/cdn/location",
        "ttsEndPointSecured": "https://ttspriv.g.comcast.net/tts?",
        "language": "en-US",
        "voice": "carol",
        "volume": "100.00",
        "rate": 5
    }
}
```
#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": {
        "TTS_Status": 0,
        "success": true
    }
}
```
<a name="method.getTTSConfiguration"></a>
## *getTTSConfiguration <sup>method</sup>*

To get the TTS Configuration.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |

### Result

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| result | object |  |
| result?.ttsEndPoint | string | <sup>*(optional)*</sup> the ttsEndPoint of TTSEngine |
| result?.ttsEndPointSecured | string | <sup>*(optional)*</sup> the ttsEndPointSecured of TTSEngine |
| result?.language | string | <sup>*(optional)*</sup> the language of TTSEngine |
| result?.voice | string | <sup>*(optional)*</sup> the voice of TTSEngine |
| result?.volume | string | <sup>*(optional)*</sup> the volume of TTSEngine |
| result?.rate | number | <sup>*(optional)*</sup> the rate of TTSEngine |

### Example

#### Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "TextToSpeech.1.getTTSConfiguration",
    "params": {}
}
```
#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": {
        "ttsEndPoint": "http://ccr.voice-guidance-tts.xcr.comcast.net/tts/v1/cdn/location",
        "ttsEndPointSecured": "https://ttspriv.g.comcast.net/tts?",
        "language": "en-US",
        "voice": "carol",
        "volume": "100.00",
        "rate": 5
    }
}
```
<a name="method.isTTSEnabled"></a>
## *isTTSEnabled <sup>method</sup>*

Check whether TTS is enabled or not.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.force | boolean | Todo NAMBI |

### Result

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| result | object |  |
| result?.isEnabled | boolean | <sup>*(optional)*</sup> Indicates TTSEngine is enabled or not |
| result?.TTS_Status | number | <sup>*(optional)*</sup> TTS Return status (must be one of the following: *TTS_OK*, *TTS_FAIL*, *TTS_NOT_ENABLED*, *TTS_CREATE_SESSION_DUPLICATE*, *TTS_EMPTY_APPID_INPUT*, *TTS_RESOURCE_BUSY*, *TTS_NO_SESSION_FOUND*, *TTS_NESTED_CLAIM_REQUEST*, *TTS_INVALID_CONFIGURATION*, *TTS_SESSION_NOT_ACTIVE*, *TTS_APP_NOT_FOUND*, *TTS_POLICY_VIOLATION*, *TTS_OBJECT_DESTROYED*, *TTS_SPEECH_NOT_FOUND*) |
| result?.success | boolean | <sup>*(optional)*</sup> Call status |

### Example

#### Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "TextToSpeech.1.isTTSEnabled",
    "params": {
        "force": true
    }
}
```
#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": {
        "isEnabled": true,
        "TTS_Status": 0,
        "success": true
    }
}
```
<a name="method.isSessionActiveForApp"></a>
## *isSessionActiveForApp <sup>method</sup>*

Check whether TTSSession is active for app or not.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.appId | number | Todo NAMBI |

### Result

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| result | object |  |
| result?.isActive | boolean | <sup>*(optional)*</sup> Indicates TTSSession is active for app or not |
| result?.TTS_Status | number | <sup>*(optional)*</sup> TTS Return status (must be one of the following: *TTS_OK*, *TTS_FAIL*, *TTS_NOT_ENABLED*, *TTS_CREATE_SESSION_DUPLICATE*, *TTS_EMPTY_APPID_INPUT*, *TTS_RESOURCE_BUSY*, *TTS_NO_SESSION_FOUND*, *TTS_NESTED_CLAIM_REQUEST*, *TTS_INVALID_CONFIGURATION*, *TTS_SESSION_NOT_ACTIVE*, *TTS_APP_NOT_FOUND*, *TTS_POLICY_VIOLATION*, *TTS_OBJECT_DESTROYED*, *TTS_SPEECH_NOT_FOUND*) |
| result?.success | boolean | <sup>*(optional)*</sup> Call status |

### Example

#### Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "TextToSpeech.1.isSessionActiveForApp",
    "params": {
        "appId": 1
    }
}
```
#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": {
        "isActive": true,
        "TTS_Status": 0,
        "success": true
    }
}
```
<a name="method.acquireResource"></a>
## *acquireResource <sup>method</sup>*

Acquire TTS Resource for app.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.appId | number | Todo NAMBI |

### Result

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| result | object |  |
| result?.TTS_Status | number | <sup>*(optional)*</sup> TTS Return status (must be one of the following: *TTS_OK*, *TTS_FAIL*, *TTS_NOT_ENABLED*, *TTS_CREATE_SESSION_DUPLICATE*, *TTS_EMPTY_APPID_INPUT*, *TTS_RESOURCE_BUSY*, *TTS_NO_SESSION_FOUND*, *TTS_NESTED_CLAIM_REQUEST*, *TTS_INVALID_CONFIGURATION*, *TTS_SESSION_NOT_ACTIVE*, *TTS_APP_NOT_FOUND*, *TTS_POLICY_VIOLATION*, *TTS_OBJECT_DESTROYED*, *TTS_SPEECH_NOT_FOUND*) |
| result?.success | boolean | <sup>*(optional)*</sup> Call status |

### Example

#### Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "TextToSpeech.1.acquireResource",
    "params": {
        "appId": 1
    }
}
```
#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": {
        "TTS_Status": 0,
        "success": true
    }
}
```
<a name="method.claimResource"></a>
## *claimResource <sup>method</sup>*

Claim TTS Resource for app.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.appId | number | Todo NAMBI |

### Result

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| result | object |  |
| result?.TTS_Status | number | <sup>*(optional)*</sup> TTS Return status (must be one of the following: *TTS_OK*, *TTS_FAIL*, *TTS_NOT_ENABLED*, *TTS_CREATE_SESSION_DUPLICATE*, *TTS_EMPTY_APPID_INPUT*, *TTS_RESOURCE_BUSY*, *TTS_NO_SESSION_FOUND*, *TTS_NESTED_CLAIM_REQUEST*, *TTS_INVALID_CONFIGURATION*, *TTS_SESSION_NOT_ACTIVE*, *TTS_APP_NOT_FOUND*, *TTS_POLICY_VIOLATION*, *TTS_OBJECT_DESTROYED*, *TTS_SPEECH_NOT_FOUND*) |
| result?.success | boolean | <sup>*(optional)*</sup> Call status |

### Example

#### Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "TextToSpeech.1.claimResource",
    "params": {
        "appId": 1
    }
}
```
#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": {
        "TTS_Status": 0,
        "success": true
    }
}
```
<a name="method.releaseResource"></a>
## *releaseResource <sup>method</sup>*

Release TTS Resource.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.appId | number | Todo NAMBI |

### Result

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| result | object |  |
| result?.TTS_Status | number | <sup>*(optional)*</sup> TTS Return status (must be one of the following: *TTS_OK*, *TTS_FAIL*, *TTS_NOT_ENABLED*, *TTS_CREATE_SESSION_DUPLICATE*, *TTS_EMPTY_APPID_INPUT*, *TTS_RESOURCE_BUSY*, *TTS_NO_SESSION_FOUND*, *TTS_NESTED_CLAIM_REQUEST*, *TTS_INVALID_CONFIGURATION*, *TTS_SESSION_NOT_ACTIVE*, *TTS_APP_NOT_FOUND*, *TTS_POLICY_VIOLATION*, *TTS_OBJECT_DESTROYED*, *TTS_SPEECH_NOT_FOUND*) |
| result?.success | boolean | <sup>*(optional)*</sup> Call status |

### Example

#### Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "TextToSpeech.1.releaseResource",
    "params": {
        "appId": 1
    }
}
```
#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": {
        "TTS_Status": 0,
        "success": true
    }
}
```
<a name="method.createSession"></a>
## *createSession <sup>method</sup>*

Create TTS Session.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params?.appName | string | <sup>*(optional)*</sup> Todo NAMBI |
| params?.appId | number | <sup>*(optional)*</sup> Todo NAMBI |

### Result

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| result | object |  |
| result?.TTSSessionId | number | <sup>*(optional)*</sup> Todo NAMBI |
| result?.TTS_Status | number | <sup>*(optional)*</sup> TTS Return status (must be one of the following: *TTS_OK*, *TTS_FAIL*, *TTS_NOT_ENABLED*, *TTS_CREATE_SESSION_DUPLICATE*, *TTS_EMPTY_APPID_INPUT*, *TTS_RESOURCE_BUSY*, *TTS_NO_SESSION_FOUND*, *TTS_NESTED_CLAIM_REQUEST*, *TTS_INVALID_CONFIGURATION*, *TTS_SESSION_NOT_ACTIVE*, *TTS_APP_NOT_FOUND*, *TTS_POLICY_VIOLATION*, *TTS_OBJECT_DESTROYED*, *TTS_SPEECH_NOT_FOUND*) |
| result?.success | boolean | <sup>*(optional)*</sup> Call status |

### Example

#### Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "TextToSpeech.1.createSession",
    "params": {
        "appName": "A",
        "appId": 1
    }
}
```
#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": {
        "TTSSessionId": 1,
        "TTS_Status": 0,
        "success": true
    }
}
```
<a name="method.destroySession"></a>
## *destroySession <sup>method</sup>*

Destroy TTS Session.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.sessionId | number | Todo NAMBI |

### Result

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| result | object |  |
| result?.TTS_Status | number | <sup>*(optional)*</sup> TTS Return status (must be one of the following: *TTS_OK*, *TTS_FAIL*, *TTS_NOT_ENABLED*, *TTS_CREATE_SESSION_DUPLICATE*, *TTS_EMPTY_APPID_INPUT*, *TTS_RESOURCE_BUSY*, *TTS_NO_SESSION_FOUND*, *TTS_NESTED_CLAIM_REQUEST*, *TTS_INVALID_CONFIGURATION*, *TTS_SESSION_NOT_ACTIVE*, *TTS_APP_NOT_FOUND*, *TTS_POLICY_VIOLATION*, *TTS_OBJECT_DESTROYED*, *TTS_SPEECH_NOT_FOUND*) |
| result?.success | boolean | <sup>*(optional)*</sup> Call status |

### Example

#### Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "TextToSpeech.1.destroySession",
    "params": {
        "sessionId": 1
    }
}
```
#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": {
        "TTS_Status": 0,
        "success": true
    }
}
```
<a name="method.isActiveSession"></a>
## *isActiveSession <sup>method</sup>*

Check whether TTSSession is active or not.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params?.forcefetch | boolean | <sup>*(optional)*</sup> Indicates TTSSession is active or not |
| params?.sessionId | number | <sup>*(optional)*</sup> Todo NAMBI |

### Result

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| result | object |  |
| result?.isActive | boolean | <sup>*(optional)*</sup> Indicates TTSSession is active or not |
| result?.TTS_Status | number | <sup>*(optional)*</sup> TTS Return status (must be one of the following: *TTS_OK*, *TTS_FAIL*, *TTS_NOT_ENABLED*, *TTS_CREATE_SESSION_DUPLICATE*, *TTS_EMPTY_APPID_INPUT*, *TTS_RESOURCE_BUSY*, *TTS_NO_SESSION_FOUND*, *TTS_NESTED_CLAIM_REQUEST*, *TTS_INVALID_CONFIGURATION*, *TTS_SESSION_NOT_ACTIVE*, *TTS_APP_NOT_FOUND*, *TTS_POLICY_VIOLATION*, *TTS_OBJECT_DESTROYED*, *TTS_SPEECH_NOT_FOUND*) |
| result?.success | boolean | <sup>*(optional)*</sup> Call status |

### Example

#### Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "TextToSpeech.1.isActiveSession",
    "params": {
        "forcefetch": true,
        "sessionId": 1
    }
}
```
#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": {
        "isActive": true,
        "TTS_Status": 0,
        "success": true
    }
}
```
<a name="method.setPreemptiveSpeak"></a>
## *setPreemptiveSpeak <sup>method</sup>*

SetPreemptiveSpeak or queeing speech.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params?.preemptive | boolean | <sup>*(optional)*</sup> Indicates preemptive mode |
| params?.sessionId | number | <sup>*(optional)*</sup> Todo NAMBI |

### Result

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| result | object |  |
| result?.TTS_Status | number | <sup>*(optional)*</sup> TTS Return status (must be one of the following: *TTS_OK*, *TTS_FAIL*, *TTS_NOT_ENABLED*, *TTS_CREATE_SESSION_DUPLICATE*, *TTS_EMPTY_APPID_INPUT*, *TTS_RESOURCE_BUSY*, *TTS_NO_SESSION_FOUND*, *TTS_NESTED_CLAIM_REQUEST*, *TTS_INVALID_CONFIGURATION*, *TTS_SESSION_NOT_ACTIVE*, *TTS_APP_NOT_FOUND*, *TTS_POLICY_VIOLATION*, *TTS_OBJECT_DESTROYED*, *TTS_SPEECH_NOT_FOUND*) |
| result?.success | boolean | <sup>*(optional)*</sup> Call status |

### Example

#### Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "TextToSpeech.1.setPreemptiveSpeak",
    "params": {
        "preemptive": true,
        "sessionId": 1
    }
}
```
#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": {
        "TTS_Status": 0,
        "success": true
    }
}
```
<a name="method.requestExtendedEvents"></a>
## *requestExtendedEvents <sup>method</sup>*

Set requestExtendedEvents.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params?.extendedEvents | number | <sup>*(optional)*</sup> Extended Events (must be one of the following: *EXT_EVENT_WILL_SPEAK*, *EXT_EVENT_PAUSED*, *EXT_EVENT_RESUMED*, *EXT_EVENT_CANCELLED*, *EXT_EVENT_INTERRUPTED*, *EXT_EVENT_NETWORK_ERROR*, *EXT_EVENT_PLAYBACK_ERROR*, *EXT_EVENT_ALL*) |
| params?.sessionId | number | <sup>*(optional)*</sup> Todo NAMBI |

### Result

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| result | object |  |
| result?.TTS_Status | number | <sup>*(optional)*</sup> TTS Return status (must be one of the following: *TTS_OK*, *TTS_FAIL*, *TTS_NOT_ENABLED*, *TTS_CREATE_SESSION_DUPLICATE*, *TTS_EMPTY_APPID_INPUT*, *TTS_RESOURCE_BUSY*, *TTS_NO_SESSION_FOUND*, *TTS_NESTED_CLAIM_REQUEST*, *TTS_INVALID_CONFIGURATION*, *TTS_SESSION_NOT_ACTIVE*, *TTS_APP_NOT_FOUND*, *TTS_POLICY_VIOLATION*, *TTS_OBJECT_DESTROYED*, *TTS_SPEECH_NOT_FOUND*) |
| result?.success | boolean | <sup>*(optional)*</sup> Call status |

### Example

#### Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "TextToSpeech.1.requestExtendedEvents",
    "params": {
        "extendedEvents": 1,
        "sessionId": 1
    }
}
```
#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": {
        "TTS_Status": 0,
        "success": true
    }
}
```
<a name="method.speak"></a>
## *speak <sup>method</sup>*

Start Speech.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params?.sessionId | number | <sup>*(optional)*</sup> Session Id |
| params?.id | number | <sup>*(optional)*</sup> SpeechId |
| params?.secure | boolean | <sup>*(optional)*</sup> Indicate secure/plain mode |
| params?.text | string | <sup>*(optional)*</sup> Text input |

### Result

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| result | object |  |
| result?.TTS_Status | number | <sup>*(optional)*</sup> TTS Return status (must be one of the following: *TTS_OK*, *TTS_FAIL*, *TTS_NOT_ENABLED*, *TTS_CREATE_SESSION_DUPLICATE*, *TTS_EMPTY_APPID_INPUT*, *TTS_RESOURCE_BUSY*, *TTS_NO_SESSION_FOUND*, *TTS_NESTED_CLAIM_REQUEST*, *TTS_INVALID_CONFIGURATION*, *TTS_SESSION_NOT_ACTIVE*, *TTS_APP_NOT_FOUND*, *TTS_POLICY_VIOLATION*, *TTS_OBJECT_DESTROYED*, *TTS_SPEECH_NOT_FOUND*) |
| result?.success | boolean | <sup>*(optional)*</sup> Call status |

### Example

#### Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "TextToSpeech.1.speak",
    "params": {
        "sessionId": 1,
        "id": 1,
        "secure": true,
        "text": "speech_1"
    }
}
```
#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": {
        "TTS_Status": 0,
        "success": true
    }
}
```
<a name="method.abort"></a>
## *abort <sup>method</sup>*

Abort the speech.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params?.sessionId | number | <sup>*(optional)*</sup> Todo NAMBI |
| params?.clearPending | boolean | <sup>*(optional)*</sup> clearPending |

### Result

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| result | object |  |
| result?.TTS_Status | number | <sup>*(optional)*</sup> TTS Return status (must be one of the following: *TTS_OK*, *TTS_FAIL*, *TTS_NOT_ENABLED*, *TTS_CREATE_SESSION_DUPLICATE*, *TTS_EMPTY_APPID_INPUT*, *TTS_RESOURCE_BUSY*, *TTS_NO_SESSION_FOUND*, *TTS_NESTED_CLAIM_REQUEST*, *TTS_INVALID_CONFIGURATION*, *TTS_SESSION_NOT_ACTIVE*, *TTS_APP_NOT_FOUND*, *TTS_POLICY_VIOLATION*, *TTS_OBJECT_DESTROYED*, *TTS_SPEECH_NOT_FOUND*) |
| result?.success | boolean | <sup>*(optional)*</sup> Call status |

### Example

#### Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "TextToSpeech.1.abort",
    "params": {
        "sessionId": 1,
        "clearPending": true
    }
}
```
#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": {
        "TTS_Status": 0,
        "success": true
    }
}
```
<a name="method.pause"></a>
## *pause <sup>method</sup>*

Pause the speech.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params?.sessionId | number | <sup>*(optional)*</sup> Todo NAMBI |
| params?.speechId | number | <sup>*(optional)*</sup> speechId |

### Result

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| result | object |  |
| result?.TTS_Status | number | <sup>*(optional)*</sup> TTS Return status (must be one of the following: *TTS_OK*, *TTS_FAIL*, *TTS_NOT_ENABLED*, *TTS_CREATE_SESSION_DUPLICATE*, *TTS_EMPTY_APPID_INPUT*, *TTS_RESOURCE_BUSY*, *TTS_NO_SESSION_FOUND*, *TTS_NESTED_CLAIM_REQUEST*, *TTS_INVALID_CONFIGURATION*, *TTS_SESSION_NOT_ACTIVE*, *TTS_APP_NOT_FOUND*, *TTS_POLICY_VIOLATION*, *TTS_OBJECT_DESTROYED*, *TTS_SPEECH_NOT_FOUND*) |
| result?.success | boolean | <sup>*(optional)*</sup> Call status |

### Example

#### Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "TextToSpeech.1.pause",
    "params": {
        "sessionId": 1,
        "speechId": 1
    }
}
```
#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": {
        "TTS_Status": 0,
        "success": true
    }
}
```
<a name="method.resume"></a>
## *resume <sup>method</sup>*

Resume the speech.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params?.sessionId | number | <sup>*(optional)*</sup> Todo NAMBI |
| params?.speechId | number | <sup>*(optional)*</sup> speechId |

### Result

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| result | object |  |
| result?.TTS_Status | number | <sup>*(optional)*</sup> TTS Return status (must be one of the following: *TTS_OK*, *TTS_FAIL*, *TTS_NOT_ENABLED*, *TTS_CREATE_SESSION_DUPLICATE*, *TTS_EMPTY_APPID_INPUT*, *TTS_RESOURCE_BUSY*, *TTS_NO_SESSION_FOUND*, *TTS_NESTED_CLAIM_REQUEST*, *TTS_INVALID_CONFIGURATION*, *TTS_SESSION_NOT_ACTIVE*, *TTS_APP_NOT_FOUND*, *TTS_POLICY_VIOLATION*, *TTS_OBJECT_DESTROYED*, *TTS_SPEECH_NOT_FOUND*) |
| result?.success | boolean | <sup>*(optional)*</sup> Call status |

### Example

#### Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "TextToSpeech.1.resume",
    "params": {
        "sessionId": 1,
        "speechId": 1
    }
}
```
#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": {
        "TTS_Status": 0,
        "success": true
    }
}
```
<a name="method.isSpeaking"></a>
## *isSpeaking <sup>method</sup>*

Check the session is speaking or not.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.sessionId | number | Todo NAMBI |

### Result

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| result | object |  |
| result?.speaking | boolean | <sup>*(optional)*</sup> Check speaking |
| result?.TTS_Status | number | <sup>*(optional)*</sup> TTS Return status (must be one of the following: *TTS_OK*, *TTS_FAIL*, *TTS_NOT_ENABLED*, *TTS_CREATE_SESSION_DUPLICATE*, *TTS_EMPTY_APPID_INPUT*, *TTS_RESOURCE_BUSY*, *TTS_NO_SESSION_FOUND*, *TTS_NESTED_CLAIM_REQUEST*, *TTS_INVALID_CONFIGURATION*, *TTS_SESSION_NOT_ACTIVE*, *TTS_APP_NOT_FOUND*, *TTS_POLICY_VIOLATION*, *TTS_OBJECT_DESTROYED*, *TTS_SPEECH_NOT_FOUND*) |
| result?.success | boolean | <sup>*(optional)*</sup> Call status |

### Example

#### Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "TextToSpeech.1.isSpeaking",
    "params": {
        "sessionId": 1
    }
}
```
#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": {
        "speaking": true,
        "TTS_Status": 0,
        "success": true
    }
}
```
<a name="method.getSpeechState"></a>
## *getSpeechState <sup>method</sup>*

Get the speech state.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params?.sessionId | number | <sup>*(optional)*</sup> Todo NAMBI |
| params?.speechId | number | <sup>*(optional)*</sup> speechId |

### Result

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| result | object |  |
| result?.speechState | number | <sup>*(optional)*</sup> SpeechState (must be one of the following: *SPEECH_PENDING*, *SPEECH_IN_PROGRESS*, *SPEECH_PAUSED*, *SPEECH_NOT_FOUND*) |
| result?.TTS_Status | number | <sup>*(optional)*</sup> TTS Return status (must be one of the following: *TTS_OK*, *TTS_FAIL*, *TTS_NOT_ENABLED*, *TTS_CREATE_SESSION_DUPLICATE*, *TTS_EMPTY_APPID_INPUT*, *TTS_RESOURCE_BUSY*, *TTS_NO_SESSION_FOUND*, *TTS_NESTED_CLAIM_REQUEST*, *TTS_INVALID_CONFIGURATION*, *TTS_SESSION_NOT_ACTIVE*, *TTS_APP_NOT_FOUND*, *TTS_POLICY_VIOLATION*, *TTS_OBJECT_DESTROYED*, *TTS_SPEECH_NOT_FOUND*) |
| result?.success | boolean | <sup>*(optional)*</sup> Call status |

### Example

#### Request

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "method": "TextToSpeech.1.getSpeechState",
    "params": {
        "sessionId": 1,
        "speechId": 1
    }
}
```
#### Response

```json
{
    "jsonrpc": "2.0",
    "id": 1234567890,
    "result": {
        "speechState": 0,
        "TTS_Status": 0,
        "success": true
    }
}
```
<a name="head.Notifications"></a>
# Notifications

Notifications are autonomous events, triggered by the internals of the implementation, and broadcasted via JSON-RPC to all registered observers.Refer to [[Thunder](#ref.Thunder)] for information on how to register for a notification.

The following events are provided by the TextToSpeech plugin:

TextToSpeech interface events:

| Event | Description |
| :-------- | :-------- |
| [onTTSStateChanged](#event.onTTSStateChanged) | Notifies about TTS state status (Enabled or Disabled) |
| [onTTSSessionCreated](#event.onTTSSessionCreated) | Notifies about TTS session is created or not |
| [onVoiceChanged](#event.onVoiceChanged) | Notifies voice changed |
| [onResourceAcquired](#event.onResourceAcquired) | Notifies when TTS Resource is acquired |
| [onResourceReleased](#event.onResourceReleased) | Notifies when TTS Resource is released |
| [onWillSpeak](#event.onWillSpeak) | Notifies when TTS Resource is acquired |
| [onSpeechStart](#event.onSpeechStart) | Notifies when speech is starts |
| [onSpeechPause](#event.onSpeechPause) | Notifies when speech pause occurred |
| [onSpeechResume](#event.onSpeechResume) | Notifies when speech Resume occurred |
| [onSpeechInterrupt](#event.onSpeechInterrupt) | Notifies when speech is interrupted |
| [onSpeechCancel](#event.onSpeechCancel) | Notifies when speech is cancelled |
| [onNetworkError](#event.onNetworkError) | Notifies when network error is occurred |
| [onPlaybackError](#event.onPlaybackError) | Notifies when playback error |
| [onSpeechComplete](#event.onSpeechComplete) | Notifies when speech is completed |

<a name="event.onTTSStateChanged"></a>
## *onTTSStateChanged <sup>event</sup>*

Notifies about TTS state status (Enabled or Disabled).

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.state | boolean | TTS Engine State |

### Example

```json
{
    "jsonrpc": "2.0",
    "method": "client.events.1.onTTSStateChanged",
    "params": {
        "state": true
    }
}
```
<a name="event.onTTSSessionCreated"></a>
## *onTTSSessionCreated <sup>event</sup>*

Notifies about TTS session is created or not.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.appId | number | AppId |
| params.sessionId | number | Session Id |

### Example

```json
{
    "jsonrpc": "2.0",
    "method": "client.events.1.onTTSSessionCreated",
    "params": {
        "appId": 1,
        "sessionId": 1
    }
}
```
<a name="event.onVoiceChanged"></a>
## *onVoiceChanged <sup>event</sup>*

Notifies voice changed.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.voice | string | Voice details |

### Example

```json
{
    "jsonrpc": "2.0",
    "method": "client.events.1.onVoiceChanged",
    "params": {
        "voice": "carol"
    }
}
```
<a name="event.onResourceAcquired"></a>
## *onResourceAcquired <sup>event</sup>*

Notifies when TTS Resource is acquired.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.appId | number | AppId |
| params.sessionId | number | Session Id |

### Example

```json
{
    "jsonrpc": "2.0",
    "method": "client.events.1.onResourceAcquired",
    "params": {
        "appId": 1,
        "sessionId": 1
    }
}
```
<a name="event.onResourceReleased"></a>
## *onResourceReleased <sup>event</sup>*

Notifies when TTS Resource is released.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.appId | number | AppId |
| params.sessionId | number | Session Id |

### Example

```json
{
    "jsonrpc": "2.0",
    "method": "client.events.1.onResourceReleased",
    "params": {
        "appId": 1,
        "sessionId": 1
    }
}
```
<a name="event.onWillSpeak"></a>
## *onWillSpeak <sup>event</sup>*

Notifies when TTS Resource is acquired.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.appId | number | AppId |
| params.sessionId | number | Session Id |
| params.speechId | number | speechId |
| params.text | string | Text |

### Example

```json
{
    "jsonrpc": "2.0",
    "method": "client.events.1.onWillSpeak",
    "params": {
        "appId": 1,
        "sessionId": 1,
        "speechId": 1,
        "text": "speech_1"
    }
}
```
<a name="event.onSpeechStart"></a>
## *onSpeechStart <sup>event</sup>*

Notifies when speech is starts.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.appId | number | AppId |
| params.sessionId | number | Session Id |
| params.speechId | number | speechId |
| params.text | string | Text |

### Example

```json
{
    "jsonrpc": "2.0",
    "method": "client.events.1.onSpeechStart",
    "params": {
        "appId": 1,
        "sessionId": 1,
        "speechId": 1,
        "text": "speech_1"
    }
}
```
<a name="event.onSpeechPause"></a>
## *onSpeechPause <sup>event</sup>*

Notifies when speech pause occurred.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.appId | number | AppId |
| params.sessionId | number | Session Id |
| params.speechId | number | Speech Id |

### Example

```json
{
    "jsonrpc": "2.0",
    "method": "client.events.1.onSpeechPause",
    "params": {
        "appId": 1,
        "sessionId": 1,
        "speechId": 1
    }
}
```
<a name="event.onSpeechResume"></a>
## *onSpeechResume <sup>event</sup>*

Notifies when speech Resume occurred.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.appId | number | AppId |
| params.sessionId | number | Session Id |
| params.speechId | number | Speech Id |

### Example

```json
{
    "jsonrpc": "2.0",
    "method": "client.events.1.onSpeechResume",
    "params": {
        "appId": 1,
        "sessionId": 1,
        "speechId": 1
    }
}
```
<a name="event.onSpeechInterrupt"></a>
## *onSpeechInterrupt <sup>event</sup>*

Notifies when speech is interrupted.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.appId | number | AppId |
| params.sessionId | number | Session Id |
| params.speechId | number | Speech Id |

### Example

```json
{
    "jsonrpc": "2.0",
    "method": "client.events.1.onSpeechInterrupt",
    "params": {
        "appId": 1,
        "sessionId": 1,
        "speechId": 1
    }
}
```
<a name="event.onSpeechCancel"></a>
## *onSpeechCancel <sup>event</sup>*

Notifies when speech is cancelled.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.appId | number | AppId |
| params.sessionId | number | Session Id |
| params.speechId | number | Speech Id |

### Example

```json
{
    "jsonrpc": "2.0",
    "method": "client.events.1.onSpeechCancel",
    "params": {
        "appId": 1,
        "sessionId": 1,
        "speechId": 1
    }
}
```
<a name="event.onNetworkError"></a>
## *onNetworkError <sup>event</sup>*

Notifies when network error is occurred.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.appId | number | AppId |
| params.sessionId | number | Session Id |
| params.speechId | number | Speech Id |

### Example

```json
{
    "jsonrpc": "2.0",
    "method": "client.events.1.onNetworkError",
    "params": {
        "appId": 1,
        "sessionId": 1,
        "speechId": 1
    }
}
```
<a name="event.onPlaybackError"></a>
## *onPlaybackError <sup>event</sup>*

Notifies when playback error.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.appId | number | AppId |
| params.sessionId | number | Session Id |
| params.speechId | number | Speech Id |

### Example

```json
{
    "jsonrpc": "2.0",
    "method": "client.events.1.onPlaybackError",
    "params": {
        "appId": 1,
        "sessionId": 1,
        "speechId": 1
    }
}
```
<a name="event.onSpeechComplete"></a>
## *onSpeechComplete <sup>event</sup>*

Notifies when speech is completed.

### Parameters

| Name | Type | Description |
| :-------- | :-------- | :-------- |
| params | object |  |
| params.appId | number | AppId |
| params.sessionId | number | Session Id |
| params.speechId | number | Speech Id |
| params.text | string | Text |

### Example

```json
{
    "jsonrpc": "2.0",
    "method": "client.events.1.onSpeechComplete",
    "params": {
        "appId": 1,
        "sessionId": 1,
        "speechId": 1,
        "text": "speech_1"
    }
}
```
