# Debugging

Ensuring smooth operation of your mining software involves automatic processes and manual interventions when necessary. Here's how you can handle typical issues that might arise during mining:

## **Reconnection Handling**

* **Automatic Reconnection:** The miner software is designed to automatically reconnect if any disconnections occur. This ensures minimal interruption in your mining activities.

## **Client Updates**

* **Automatic Updates:** Your miner software will update itself automatically after the current mining run completes. This is to ensure that you always operate with the latest features and fixes.
* **Manual Update Procedure:**
  * If the automatic update fails, you may need to update the software manually. First, terminate the ongoing training process.
  *   Run the following commands in your terminal:

      ```bash
      git pull
      make install
      ```

## Common Errors and Solutions

Encountering errors is a part of any technical process. Below are some common errors you might face and the recommended solutions:

1. **\[SSL Error]:**
   * **Cause:** This error typically indicates a problem with the VPN or network, such as slow speeds or a complete outage.
   * **Solution:** Check your network or VPN settings, and ensure a stable and fast upload is available.
2. **\[Failed to Init Particle Error]:**
   * **Cause:** This may occur if the Nimble network is down or you are experiencing rate limiting.
   * **Solution:** Wait for a while before retrying, to see if the issue resolves itself as network conditions improve. Otherwise jump in discord channel and check announcements.&#x20;
3. **\[Pydantic Error]:**
   * **Cause:** This error suggests that your client version is outdated.
   * **Solution:** Update your client software manually using the commands provided in the Client Updates section above.
