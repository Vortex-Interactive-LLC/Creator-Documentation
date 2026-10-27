---
title: ReplicatedStorage
description: Contains instances that are loaded by both the server and the client.
---

## Summary

`ReplicatedStorage` is a container for items that should be visible to both the
server and the client. Items placed here will automatically get their
properties synced from the server.

## Testing Notes

These observations are from Vortex Studio 0.8.1 and may differ in later
releases.

A temporary `Part` can be parented to `ReplicatedStorage`, and
`WaitForChild` resolves it.
