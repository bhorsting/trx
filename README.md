trx: Realtime audio over IP
===

Fork of the http://www.pogo.org.uk/~mark/trx/
(C) Copyright 2012 Mark Hills <mark@xwax.org>

See the COPYING file for licensing terms.

This software is distributed from the following URL:

  http://www.pogo.org.uk/~mark/trx/

trx is a simple toolset for broadcasting live audio. It is based on
the Opus codec <http://www.opus-codec.org/> and sends and receives
encoded audio over IP networks.

It can be used for point-to-point audio links or multicast,
eg. private transmitter links or audio distribution. In contrast to
traditional streaming, high quality wideband audio (such as music) can
be sent with low-latency and fast recovery from dropouts.

With quality audio hardware and wired ethernet, a total latency of no
more than a few milliseconds is possible.

Why this fork?
===
The original version had a hardcoded `SND_PCM_FORMAT_FLOAT` constant as PCM sample format. First this constant is deprecated (see [alsa-project.org](http://www.alsa-project.org/alsa-doc/alsa-lib/group___p_c_m.html#gaa14b7f26877a812acbb39811364177f8) for reference) and second float PCM sample format is quite unusual for current USB Audio Interfaces. 

Currently changed this to hardcoded `SND_PCM_FORMAT_S16_LE` constant and moved from `opus_encode_float()` / `opus_decode_float()` to `opus_encode()` / `opus_decode()` to make libopus work with integer encoded PCM samples. 

I'm going to make this tool more configurable in the future (e.g. configurable PCM sample format) as I'm going to use this a lot in one of my projects.
