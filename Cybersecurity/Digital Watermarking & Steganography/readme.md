# Digital watermarking 
The **process of embedding hidden information, called a watermark, into digital media** such as images, audio, videos, or documents.

**Two applications are**:
- **Copyright protection** – proves ownership of digital content.
- **Content authentication** – verifies whether digital content has been modified or tampered with.

**Basic Flow:**
```
 Watermark + Host Media
        ↓
  Embedding Algorithm + Secret Key
        ↓
  Watermarked Media
        ↓
Transmission / Storage
        ↓
Detection / Extraction
        ↓
Ownership / Authentication
```

**Types of Watermarking:**
- **Robust watermarking** focuses on survival.
- **Fragile watermarking** focuses on detecting changes.

**Imperceptibility** ensures that the **watermark does not noticeably reduce the quality of the original media**. This keeps the image, audio, or video usable and attractive.

#Steganography 
The **technique of hiding a secret message inside a cover medium** such as an image, audio file, video, or text document. It's **primary purpose is to hide the existence of the secret information**, rather than simply hiding its contents through encryption. The **resulting file is called a stego object** and appears almost identical to the original cover file.

**Types of Extraction:**
**Blind Extraction:**
The receiver extracts the hidden message **without requiring the original cover object**. The stego object and the required key/algorithm are used for extraction.

**Informed Extraction:**
The receiver **uses additional information about the original cover or embedding process during extraction**, which can help recover the hidden information more accurately.

**Statistical undetectability** means that the **stego object should be statistically indistinguishable from the original cover object.** This makes detection by statistical steganalysis difficult.

**Benchmarking**
**Testing and comparing watermarking systems** using common performance criteria. helps developers compare different watermarking techniques and select a suitable technique for a particular application.

**Embedding capacity** is the amount of secret information that can be hidden inside a cover medium.

Message coding is the **process of converting the original message into a coded/binary representation** before watermark embedding.

A message vector is the **mathematical representation of this coded message** as a sequence of numbers or bits.

Error Correction Coding (ECC) **adds redundant bits to the watermark before embedding.

**Communication-based model:**
Treats watermark embedding similar to digital communication.
The **watermark acts like information being transmitted through a communication channel. The media and possible distortions act like the communication environment,** while the detector recovers the watermark at the receiver side.

**geometric transformation is an operation that changes the position, orientation, size, or shape of digital content**. Examples include rotation, scaling, cropping, translation, and resizing.

Synchronisation in a template based geometric model
Transformation → Estimate → Realign → Detect

**Spatial domain**: represents an image directly using its **pixels and their positions** such as (x, y).

**Polar coordinate domain**: represents positions using **distance from a reference point (radius) and angle (θ).**

Mapping Process: 
Original Message → Binary Conversion/Encoding → Message Mapping → Message Vector → Watermark Embedding

**Side information** may include host-media characteristics, secret keys, watermark patterns, image features, and statistical properties.

**Dirty-Paper Coding (DPC)** uses the known host media as side information/interference during watermark embedding.

Types of Distortions:
- **Volumetric distortion**: Changes the **pixel/signal values** of the media, such as noise or filtering.
- **Temporal distortion**: Affects the **time sequence**, mainly in audio and video, such as frame reordering.
- **Geometric distortion**: Changes the **position, orientation, or size**, such as rotation, scaling, and cropping.

**Resist geometric attacks**:
- synchronization techniques
- feature-based watermarking
- DFT/DWT and Error Correction Coding (ECC)

**Redundant embedding**:
The **same watermark information is embedded multiple times in different locations of the host media**.

**Lattice Codes embed and decode watermark information**
- During embedding, the host media is treated as known interference, and the **encoder maps the watermark information to suitable points in a lattice while considering the host signal**.
- During decoding, the **received signal is examined and the nearest/appropriate lattice point is selected to recover the watermark information**.

**Spread Spectrum Coding** is a watermarking technique in which the **watermark is distributed over a large number of host-signal components** using a pseudo-random (PN) sequence. The **PN sequence is generated using a secret key, and the watermark is spread across many pixels or coefficients.**

**Scalar watermarking** embeds information by slightly modifying individual numerical values according to the watermark bits.

