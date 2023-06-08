---
title: Support Tunnel Cluster Logs
toc: false
permalink: support_tunnel.html
---

## Requirements

- Opening or closing a support tunnel via the **Remote Support** tab in the **Control Center** will create a cluster log with the following information:
    * User who opened/closed the tunnel 
    * Node the tunnel was opened/closed on 
    * Code associated with the open tunnel 
- Opening or closing a support tunnel via the **Login Screen** before logging in should create a cluster log with the following information:
    * “Login Screen from `<IP address of machine that did the action>`” as the user who opened/closed the tunnel 
    * Node the tunnel was opened/closed on 
    * Code associated with the open tunnel 
- Opening or closing a support tunnel via an API call where the user cannot be passed to the **HyperCore UI** should create a cluster log with the following information:
    * `Unauthenticated` as the user who opened/closed the tunnel 
    * Node the tunnel was opened/closed on 
    * Code associated with the open tunnel 

