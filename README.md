<div align="left">

[![Visit Front](./header.png)](https://front.com)

# [Front](https://front.com)<a id="front"></a>

Front is a customer operations platform that enables support, sales, and account management teams to deliver exceptional service at scale. Front streamlines customer communication by combining the efficiency of a help desk and the familiarity of email, with automated workflows and real-time collaboration behind the scenes.

With Front, teams can centralize messages across channels, route them to the right person, and unlock visibility and insights across all of their customer operations. More than 8000 businesses use Front to drive operational efficiency that prevents churn, improves retention, and propels customer growth.

</div>

## Table of Contents<a id="table-of-contents"></a>

<!-- toc -->

- [Installation](#installation)
- [Getting Started](#getting-started)
- [Reference](#reference)
  * [`frontchannel.channels.updateChannel`](#frontchannelchannelsupdatechannel)
  * [`frontchannel.messages.importReceivedMessage`](#frontchannelmessagesimportreceivedmessage)
  * [`frontchannel.messages.importSyncedMessage`](#frontchannelmessagesimportsyncedmessage)

<!-- tocstop -->

## Installation<a id="installation"></a>
<div align="center">
  <a href="https://konfigthis.com/sdk-sign-up?company=Front&serviceName=Channel&language=TypeScript">
    <img src="https://raw.githubusercontent.com/konfig-dev/brand-assets/HEAD/cta-images/typescript-cta.png" width="70%">
  </a>
</div>

## Getting Started<a id="getting-started"></a>

```typescript
import { FrontChannel } from "front-channel-typescript-sdk";

const frontchannel = new FrontChannel({
  // Defining the base path is optional and defaults to https://api2.frontapp.com
  // basePath: "https://api2.frontapp.com",
  accessToken: "ACCESS_TOKEN",
});

const updateChannelResponse = await frontchannel.channels.updateChannel({
  channelId: "cha_123",
  status: "offline",
});

console.log(updateChannelResponse);
```

## Reference<a id="reference"></a>


### `frontchannel.channels.updateChannel`<a id="frontchannelchannelsupdatechannel"></a>

Update a channel.

#### 🛠️ Usage<a id="🛠️-usage"></a>

```typescript
const updateChannelResponse = await frontchannel.channels.updateChannel({
  channelId: "cha_123",
  status: "offline",
});
```

#### ⚙️ Parameters<a id="⚙️-parameters"></a>

##### channelId: `string`<a id="channelid-string"></a>

The Channel ID. Alternatively, you can supply the channel address as a [resource alias](https://dev.frontapp.com/docs/resource-aliases-1).

##### status: `string`<a id="status-string"></a>

Status of the channel

#### 🌐 Endpoint<a id="🌐-endpoint"></a>

`/channels/{channel_id}` `PATCH`

[🔙 **Back to Table of Contents**](#table-of-contents)

---


### `frontchannel.messages.importReceivedMessage`<a id="frontchannelmessagesimportreceivedmessage"></a>

Import a message that was received by the channel.

#### 🛠️ Usage<a id="🛠️-usage"></a>

```typescript
const importReceivedMessageResponse =
  await frontchannel.messages.importReceivedMessage({
    channelId: "cha_123",
    sender: {
      handle: "handle_example",
    },
    body: "body_example",
    metadata: {
      external_id: "external_id_example",
      external_conversation_id: "external_conversation_id_example",
    },
  });
```

#### ⚙️ Parameters<a id="⚙️-parameters"></a>

##### sender: [`InboundMessageSender`](./models/inbound-message-sender.ts)<a id="sender-inboundmessagesendermodelsinbound-message-senderts"></a>

##### body: `string`<a id="body-string"></a>

Body of the message

##### metadata: [`InboundMessageMetadata`](./models/inbound-message-metadata.ts)<a id="metadata-inboundmessagemetadatamodelsinbound-message-metadatats"></a>

##### channelId: `string`<a id="channelid-string"></a>

The channel ID. Alternatively, you can supply the channel address as a [resource alias](https://dev.frontapp.com/docs/resource-aliases-1).

##### subject: `string`<a id="subject-string"></a>

Subject of the message

##### delivered_at: `number`<a id="delivered_at-number"></a>

Time in seconds at which message was created in external system

##### attachments: `Uint8Array | File | buffer.File`[]<a id="attachments-uint8array--file--bufferfile"></a>

Binary data of attached files. Must use `Content-Type: multipart/form-data` if specified. See [example](https://gist.github.com/hdornier/e04d04921032e98271f46ff8a539a4cb) or read more about [Attachments](https://dev.frontapp.com/docs/attachments-1).  Max 25 MB.

#### 🔄 Return<a id="🔄-return"></a>

[MessagesImportReceivedMessageResponse](./models/messages-import-received-message-response.ts)

#### 🌐 Endpoint<a id="🌐-endpoint"></a>

`/channels/{channel_id}/inbound_messages` `POST`

[🔙 **Back to Table of Contents**](#table-of-contents)

---


### `frontchannel.messages.importSyncedMessage`<a id="frontchannelmessagesimportsyncedmessage"></a>

Import a message that was sent from the channel.

#### 🛠️ Usage<a id="🛠️-usage"></a>

```typescript
const importSyncedMessageResponse =
  await frontchannel.messages.importSyncedMessage({
    channelId: "cha_123",
    to: [
      {
        handle: "handle_example",
      },
    ],
    body: "body_example",
    metadata: {
      external_id: "external_id_example",
      external_conversation_id: "external_conversation_id_example",
    },
  });
```

#### ⚙️ Parameters<a id="⚙️-parameters"></a>

##### to: [`OutboundMessageToInner`](./models/outbound-message-to-inner.ts)[]<a id="to-outboundmessagetoinnermodelsoutbound-message-to-innerts"></a>

Data of the message recipient

##### body: `string`<a id="body-string"></a>

Body of the message

##### metadata: [`InboundMessageMetadata`](./models/inbound-message-metadata.ts)<a id="metadata-inboundmessagemetadatamodelsinbound-message-metadatats"></a>

##### channelId: `string`<a id="channelid-string"></a>

The channel ID. Alternatively, you can supply the channel address as a [resource alias](https://dev.frontapp.com/docs/resource-aliases-1).

##### sender_name: `string`<a id="sender_name-string"></a>

Name of the sender

##### subject: `string`<a id="subject-string"></a>

Subject of the message

##### author_id: `string`<a id="author_id-string"></a>

ID of the teammate on behalf of whom the message is sent

##### delivered_at: `number`<a id="delivered_at-number"></a>

Time in seconds at which message was created in external system

##### attachments: `Uint8Array | File | buffer.File`[]<a id="attachments-uint8array--file--bufferfile"></a>

Binary data of attached files. Must use `Content-Type: multipart/form-data` if specified. See [example](https://gist.github.com/hdornier/e04d04921032e98271f46ff8a539a4cb) or read more about [Attachments](https://dev.frontapp.com/docs/attachments-1).  Max 25 MB.

#### 🔄 Return<a id="🔄-return"></a>

[MessagesImportReceivedMessageResponse](./models/messages-import-received-message-response.ts)

#### 🌐 Endpoint<a id="🌐-endpoint"></a>

`/channels/{channel_id}/outbound_messages` `POST`

[🔙 **Back to Table of Contents**](#table-of-contents)

---


## Author<a id="author"></a>
This TypeScript package is automatically generated by [Konfig](https://konfigthis.com)
