# **Hello! 👋**

Welcome to my project on the use of **Consistent Diffusion Models** for **MNIST** and **Fashion-MNIST** datasets!

I did this a while ago, and it's a piece of work that is most personal to me. The journey here was not easy, with plenty of frustrating failures along the way. I spent hours and hours testing, debugging, and staring at white clumps of noise instead of pretty generated images. 😅 But through all of that, I'm happy to have reached this far and be able to share it with all of you.

## **What is this project about?**

Briefly, it's my take on a **Denoising Diffusion Probabilistic Model (DDPM)**, one of a group of generative models that learn to produce new data by reversing an operation of adding noise. Think of it like having a blurry, noisy picture and asking a model to "un-blur" it, step by step, until a clear image emerges. 🖼️

The core of this project is a **`SimpleUNet`** model, which is the network that performs the prediction and noise removal at each step. To further improve the robustness of the model and improve the quality of the generated images, I've also incorporated an **`ImprovedRefinementNetwork`**. This network takes the original denoised image and "refines" it once more to produce a sharper, more accurate output.

## **Key Components**

* **`SimpleUNet`**: A basic **U-Net** architecture. It takes a noisy image and timestep as input, and it's trained to predict the added noise. The encoder-decoder structure of the U-Net with skip connections is well suited for such an operation as it retains important spatial information.

* **`ImprovedRefinementNetwork`**: After `SimpleUNet` finishes its work, this network takes over. It's a two-step model that further refines the output, making the final images even finer. It also uses skip connections to produce high-quality outputs.

* **Noise Scheduling**: I experimented with a range of noise schedules, from a simple linear schedule to more advanced cosine schedule. The **cosine schedule** was very efficient in this case and kept the balance in the training process and prevented the model from getting stuck.

* **Training and Sampling**: The notebook includes all the code for adding noise (**forward diffusion process**) and sampling an image back (**reverse sampling process**). I also set up a training loop that takes advantage of multiple GPUs if you have them to speed up the process.

## **What I Learned**

This was an excellent learning experience. It was not so much about coding; it was a deep dive into the real-world challenges of training generative models. I learned:

* **The importance of accurate deployment**: It requires a great deal of attention to detail to deploy a diffusion model, from network architecture to noise schedule. Tiny mistakes can equal giant mistakes (**hello, white blobs!**).

* **The power of architecture**: The U-Net architecture is a beast, and discovering how its skip connections help with information flow was crucial.

* **Patience and persistence**: As I mentioned, I experienced a lot of failures. The project made me patient, debug my code step by step, and not give up when it did not work the first time.

* **The beauty of the diffusion process**: Watching the model change from pure noise to a clear image is very satisfying and really makes the aesthetic of this technique properly sink in. ✨

I hope you enjoy exploring the code and seeing the results. Feel free to reach out with any questions or feedback!
