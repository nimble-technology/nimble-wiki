# For AI Developers

Starting your journey, you will first connect to the development environment tailored for our platform. Begin by working on a small proof of concept to familiarize yourself with our tools and workflows. Once comfortable, you can proceed to train an actual model that leverages our decentralized resources. After training, you will publish your model to the blockchain, ensuring it is securely stored and verified. Finally, deploy your model directly to the chain, allowing it to be accessed and utilized by users across the network. This streamlined process is designed to support you from initial concept through to full deployment.

## **Developing Your Proof of Concept**

Once you have a functioning proof of concept, it’s important to consider the subsequent steps needed to scale your project effectively. Read this section carefully to ensure you understand the full workflow.

## **Scaling GPUs**

**Training Large Models:** As you transition from training smaller models to large-scale models (ranging from 1 billion to 70 billion parameters), you may find that the default GPU is insufficient.

**GPU Upgrade:** To accommodate larger models, click the "upgrade" button. This will prompt the system to analyze your code and automatically assign an appropriate GPU, or possibly a group of GPUs, that best fits your requirements.

## **Model Training Progress**

**Successful Upgrade Notification:** You will receive a few msgs indicating the status the the training, i.e. waiting, started,  executing, completed, etc.&#x20;

**Continuous Operation:** Avoid interrupting the process or restarting the kernel once training has commenced. Interruptions can halt ongoing processes. Depending on the complexity and size of the job, the training might take anywhere from a few minutes to a few hours before timing out.&#x20;

**Automatic Shutdown:** To efficiently manage resources, long idle will be automatically terminated. This policy ensures resource availability for other users on the network.

## **Model Persistence**

**Temporary Storage:** Model checkpoint files are temporarily saved to ensure data integrity during training sessions.

**Long-Term Storage:** If you require access to these files for longer than three days, use the command-line interface (CLI) to download the files to your local machine, or to upgrade to Nimble's network. Detailed instructions on this process are available in a later section.
