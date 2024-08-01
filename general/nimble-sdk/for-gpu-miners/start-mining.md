# Start mining

### Verify Virtual Environment Activation

Before initiating the mining process, it is crucial to ensure that your virtual environment is correctly set up and active. This step is essential across all operating systems.

1. **Check Virtual Environment:**
   * Open your terminal or command line interface.
   * Look for the name of the virtual environment, `nimenv_localminers`, in your shell prompt. If you see it, this indicates that the virtual environment is active and properly configured.

### Start Mining

Once you have confirmed that your virtual environment is active, you can begin the mining process.

*   In your terminal, execute the following command, replacing `<copy paste your “nimblexxx” wallet address here>` with your actual Nimble Network wallet address:

    ```bash
    make run addr=<your “nimblexxx” wallet address>
    ```
* After initiating the command, look for a progress bar that indicates the status of the training job. The appearance of the progress bar means that your mining operation is running smoothly.

### Post-Training Submission

Once the training job completes, it may take several minutes for the results to be compiled and submitted to the validators. This submission is crucial for your contributions to be recognized and rewarded within the Nimble Network.

### Summary

By following these steps, you ensure that your setup is correct and that you are actively participating in the mining process. If you encounter any issues or need further assistance, consult the troubleshooting section or reach out to support.

On any OS, make sure you see the virtual env `nimenv_localminers` is in the shell.  If you see it, it means it's active.&#x20;
