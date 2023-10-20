# SwiftOpenAI
<img width="1090" alt="repoOpenAI" src="https://github.com/jamesrochabrun/SwiftOpenAI/assets/5378604/51bc5736-a32f-4a9f-922e-209d950e28f7">

![iOS 15+](https://img.shields.io/badge/iOS-15%2B-blue.svg)
[![MIT license](https://img.shields.io/badge/License-MIT-blue.svg)](https://lbesson.mit-license.org/)
[![swift-version](https://img.shields.io/badge/swift-5.9-brightgreen.svg)](https://github.com/apple/swift)
[![swiftui-version](https://img.shields.io/badge/swiftui-brightgreen)](https://developer.apple.com/documentation/swiftui)
[![xcode-version](https://img.shields.io/badge/xcode-15%20-brightgreen)](https://developer.apple.com/xcode/)
[![swift-package-manager](https://img.shields.io/badge/package%20manager-compatible-brightgreen.svg?logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPHN2ZyB3aWR0aD0iNjJweCIgaGVpZ2h0PSI0OXB4IiB2aWV3Qm94PSIwIDAgNjIgNDkiIHZlcnNpb249IjEuMSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB4bWxuczp4bGluaz0iaHR0cDovL3d3dy53My5vcmcvMTk5OS94bGluayI+CiAgICA8IS0tIEdlbmVyYXRvcjogU2tldGNoIDYzLjEgKDkyNDUyKSAtIGh0dHBzOi8vc2tldGNoLmNvbSAtLT4KICAgIDx0aXRsZT5Hcm91cDwvdGl0bGU+CiAgICA8ZGVzYz5DcmVhdGVkIHdpdGggU2tldGNoLjwvZGVzYz4KICAgIDxnIGlkPSJQYWdlLTEiIHN0cm9rZT0ibm9uZSIgc3Ryb2tlLXdpZHRoPSIxIiBmaWxsPSJub25lIiBmaWxsLXJ1bGU9ImV2ZW5vZGQiPgogICAgICAgIDxnIGlkPSJHcm91cCIgZmlsbC1ydWxlPSJub256ZXJvIj4KICAgICAgICAgICAgPHBvbHlnb24gaWQ9IlBhdGgiIGZpbGw9IiNEQkI1NTEiIHBvaW50cz0iNTEuMzEwMzQ0OCAwIDEwLjY4OTY1NTIgMCAwIDEzLjUxNzI0MTQgMCA0OSA2MiA0OSA2MiAxMy41MTcyNDE0Ij48L3BvbHlnb24+CiAgICAgICAgICAgIDxwb2x5Z29uIGlkPSJQYXRoIiBmaWxsPSIjRjdFM0FGIiBwb2ludHM9IjI3IDI1IDMxIDI1IDM1IDI1IDM3IDI1IDM3IDE0IDI1IDE0IDI1IDI1Ij48L3BvbHlnb24+CiAgICAgICAgICAgIDxwb2x5Z29uIGlkPSJQYXRoIiBmaWxsPSIjRUZDNzVFIiBwb2ludHM9IjEwLjY4OTY1NTIgMCAwIDE0IDYyIDE0IDUxLjMxMDM0NDggMCI+PC9wb2x5Z29uPgogICAgICAgICAgICA8cG9seWdvbiBpZD0iUmVjdGFuZ2xlIiBmaWxsPSIjRjdFM0FGIiBwb2ludHM9IjI3IDAgMzUgMCAzNyAxNCAyNSAxNCI+PC9wb2x5Z29uPgogICAgICAgIDwvZz4KICAgIDwvZz4KPC9zdmc+)](https://github.com/apple/swift-package-manager)

An open-source Swift package designed for effortless interaction with OpenAI's public API. 

## Table of Contents
- [Description](#description)
- [Getting an API Key](#getting-an-api-key)
- [Installation](#installation)
- [Usage](#usage)

## Description

`SwiftOpenAI` is an open-source Swift package that streamlines interactions with **all** OpenAI's API endpoints.

### OpenAI ENDPOINTS

- [Audio](#audio)
- [Chat](#chat)
- [Embeddings](#embeddings)
- [Fine-tuning](#fine-tuning)
- [Files](#files)
- [Images](#images)
- [Models](#models)
- [Moderations](#moderations)

## Getting an API Key

⚠️ **Important**

To interact with OpenAI services, you'll need an API key. Follow these steps to obtain one:

1. Visit [OpenAI](https://www.openai.com/).
2. Sign up for an [account](https://platform.openai.com/signup) or [log in](https://platform.openai.com/login) if you already have one.
3. Navigate to the [API key page](https://platform.openai.com/account/api-keys) and follow the instructions to generate a new API key.

For more information, consult OpenAI's [official documentation](https://platform.openai.com/docs/).

## Installation

### Swift Package Manager

1. Open your Swift project in Xcode.
2. Go to `File` ->  `Add Package Dependency`.
3. In the search bar, enter [this URL](https://github.com/jamesrochabrun/SwiftOpenAI).
4. Choose the version you'd like to install.
5. Click `Add Package`.

## Usage

To use SwiftOpenAI in your project, first import the package:

```swift
import SwiftOpenAI
```

Then, initialize the service using your OpenAI API key:

```swift
let apiKey = "your_openai_api_key_here"
let service = OpenAIServiceFactory.service(apiKey: apiKey)
```

You can optionally specify an organization name if needed.

```swift
let apiKey = "your_openai_api_key_here"
let oganizationID = "your_organixation_id"
let service = OpenAIServiceFactory.service(apiKey: apiKey, organizationID: oganizationID)
```

That's all you need to begin accessing the full range of OpenAI endpoints.

### Audio

#### Audio Transcriptions
Parameters
```swift
public struct AudioTranscriptionParameters: Encodable {
   
   /// The name of the file asset is not documented in OpenAI's official documentation; however, it is essential for constructing the multipart request.
   let fileName: String
   /// The audio file object (not file name) translate, in one of these formats: flac, mp3, mp4, mpeg, mpga, m4a, ogg, wav, or webm.
   let file: Data
   /// ID of the model to use. Only whisper-1 is currently available.
   let model: String
   /// The language of the input audio. Supplying the input language in [ISO-639-1](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) format will improve accuracy and latency.
   let language: String?
   /// An optional text to guide the model's style or continue a previous audio segment. The [prompt](https://platform.openai.com/docs/guides/speech-to-text/prompting) should match the audio language.
   let prompt: String?
   /// The format of the transcript output, in one of these options: json, text, srt, verbose_json, or vtt. Defaults to json
   let responseFormat: String?
   /// The sampling temperature, between 0 and 1. Higher values like 0.8 will make the output more random, while lower values like 0.2 will make it more focused and deterministic. If set to 0, the model will use [log probability](https://en.wikipedia.org/wiki/Log_probability) to automatically increase the temperature until certain thresholds are hit. Defaults to 0
   let temperature: Double?
   
   public enum Model: String {
      case whisperOne = "whisper-1"
   }
   
   enum CodingKeys: String, CodingKey {
      case file
      case model
      case prompt
      case responseFormat = "response_format"
      case temperature
      case language
   }
   
   public init(
      fileName: String,
      file: Data,
      model: Model = .whisperOne,
      prompt: String? = nil,
      responseFormat: String? = nil,
      temperature: Double? = nil,
      language: String? = nil)
   {
      self.fileName = fileName
      self.file = file
      self.model = model.rawValue
      self.prompt = prompt
      self.responseFormat = responseFormat
      self.temperature = temperature
      self.language = language
   }
}
```

Response
```swift
public struct AudioObject: Decodable {
   
   /// The transcribed text if the request uses the `transcriptions` API, or the translated text if the request uses the `translations` endpoint.
   public let text: String
}
```

Usage
```swift
let fileName = "narcos.m4a"
let data = Data(contentsOfURL:_) // Data retrieved from the file named "narcos.m4a".
let parameters = AudioTranscriptionParameters(fileName: fileName, file: data) // **Important**: in the file name always provide the file extension.
let audioObject =  try await service.createTranscription(parameters: parameters)
```
#### Audio Translations
Parameters
```swift
public struct AudioTranslationParameters: Encodable {
   
   /// The name of the file asset is not documented in OpenAI's official documentation; however, it is essential for constructing the multipart request.
   let fileName: String
   /// The audio file object (not file name) translate, in one of these formats: flac, mp3, mp4, mpeg, mpga, m4a, ogg, wav, or webm.
   let file: Data
   /// ID of the model to use. Only whisper-1 is currently available.
   let model: String
   /// An optional text to guide the model's style or continue a previous audio segment. The [prompt](https://platform.openai.com/docs/guides/speech-to-text/prompting) should match the audio language.
   let prompt: String?
   /// The format of the transcript output, in one of these options: json, text, srt, verbose_json, or vtt. Defaults to json
   let responseFormat: String?
   /// The sampling temperature, between 0 and 1. Higher values like 0.8 will make the output more random, while lower values like 0.2 will make it more focused and deterministic. If set to 0, the model will use [log probability](https://en.wikipedia.org/wiki/Log_probability) to automatically increase the temperature until certain thresholds are hit. Defaults to 0
   let temperature: Double?
   
   public enum Model: String {
      case whisperOne = "whisper-1"
   }
   
   enum CodingKeys: String, CodingKey {
      case file
      case model
      case prompt
      case responseFormat = "response_format"
      case temperature
   }
   
   public init(
      fileName: String,
      file: Data,
      model: Model = .whisperOne,
      prompt: String? = nil,
      responseFormat: String? = nil,
      temperature: Double? = nil)
   {
      self.fileName = fileName
      self.file = file
      self.model = model.rawValue
      self.prompt = prompt
      self.responseFormat = responseFormat
      self.temperature = temperature
   }
}
```

Response
```swift
public struct AudioObject: Decodable {
   
   /// The transcribed text if the request uses the `transcriptions` API, or the translated text if the request uses the `translations` endpoint.
   public let text: String
}
```

Usage
```swift
let fileName = "german.m4a"
let data = Data(contentsOfURL:_) // Data retrieved from the file named "german.m4a".
let parameters = AudioTranslationParameters(fileName: fileName, file: data) // **Important**: in the file name always provide the file extension.
let audioObject = try await service.createTranslation(parameters: parameters)
```

### Chat
### Embeddings
### Fine-tuning
### Files
### Images
### Models
### Moderations

