---
title: "Home"
menu: "main"
weight: 1
---

# A new plan with Reticulum

> Every fire begins with a single spark

## The elephants in the room

[Meshtastic](https://meshtastic.org/) is a pioneer of mesh networks leveraging cheap commodity hardware such as the ESP32 tied with long-range radio chirps over LoRA. It sparked a new generation of hobbyists and radio nerds, dreaming of off-grid, long range communication without relying on cellular networks.

In execution, Meshtastic has major limitations with increasing density.  Messages fall into black holes where node density is too high, and messages can only travel so far before exhausting their time to live (TTL). Sometimes messages make it, sometimes they don't.

Enter [MeshCore](https://meshcore.co.uk), pushing the boundaries of routing traffic over an endless sea of low bandwidth nodes, it attempts to repair Meshtastic's problems with improved packet routing. MeshCore however is not compatible with Meshtastic, dividing the LoRA communication ecosystem between a long-established player who refuses to fundamentally improve, and a passionately run project with large egos and "Freemium" paid firmware builds.

## Why just LoRA?

Radio nerds (rightfully) get excited to see Meshtastic chirps transverse tens of miles. Having Meshtastic MQTT uplink or downlink enabled is generally frowned upon as it wallpapers over undelivered messages and what is seen as "inadequate" connectivity.

Technical users like the feeling of simple communication. "Point A to B, sometimes C". However, this is **NOT** how our current modern communications grid is built. Data flows over fiber, cable, ethernet, wifi, satellite.

## Enter Reticulum

Reticulum removes the communication reliance on a single link or node. Traffic flows through the Reticulum mesh via LoRA, Wifi, LTE, GPRS, Ethernet, TCP, UDP, VHF, UHF, Serial.

*What about grid down* situations I hear you ask?  We shouldn't be choosing one physical connectivity layer to get messages through. The chances of **all** communications being down, on every medium, at a global scale are minimal. We should be aiming to use the "highest bandwidth tier" available. If that's WIFI, great. If that's LoRA? That's great too.

> If they really wanted to silence you, they would just remove the 900 Mhz spectrum (or flood it with trash).

Reticulum is designed to work reliably in open, trustless environments.  Users can join, and leave in a free and unorganized manner.

## Reticulum network node types

* Backbone nodes
  * Very fast, resource efficient Reticulum instances running in stable locations
  * Bridges groupings of Reticulum nodes spread apart geographically
  * Essentially Meshtastic's MQTT uplink / downlink... but actually part of the network and able to route traffic.
* Everyone else
  * Generally what *you* run.  Attaches to backbones, attaches to Wifi, LoRA Radios, Ethernet, "any phy you can dream up".
  * RNode - A simple radio modem firmware for low-end ESP32 devices. Does *NOT* route traffic given hardware limitations. Attaches to full Reticulum instances.
  * RNodeTH4 - A self-contained Reticulum boundary node based on the Heltec v3 or v4
    * The Heltec v3 and v4 devices ship with external PSRAM, which enables routing tables to be stored.

## So how do we do it?

Reticulum is feature complete in a drafted standard, and a python implementation.
For Reticulum to grow however, compiled implementations need contributions and improvements. C, Go, Rust.

## More Information

### Protocol

* https://reticulum.network - Core Protocol
* https://directory.rns.recipes - Map of known public interfaces
* https://rmap.world - Map of instances

### Nodes
* https://unsigned.io/rnode/ - Original RNode ESP32 "modem"
* https://github.com/jrl290/RNodeTHV4 - Self contained boundary node for Heltec v3, v4.

### Applications
* https://github.com/torlando-tech/columba - Columba messenger for Reticulum
* https://github.com/markqvist/NomadNet - Nomad network (BBS, chat, terminal based)
