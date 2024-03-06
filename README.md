In order to paralelize the code provided in the tema1.c file, the main and rescale functions were modified, while adding the threads_data function and the thread_func function.

The thread_data structure is defined as follows:

- N: An integer representing the size of the image.
- P: An integer representing the number of threads.
- thread_id: An integer uniquely identifying the thread.
- image: A pointer to a ppm_image structure, which represents the input image.
- new_image: A pointer to a ppm_image structure, which represents the rescaled image.

The main function was modified so that it will store the P (number of threads) in the data (of thread_data_t type) structure that was also declared. It also sends the whole data structure to the rescale function, not just the ppm_image image pointer.

The rescale function was modified so that it accepts thread_data_t inputs, while storing the ppm_image new_image pointer in the data structure provided in input. The ability to create multiple threads to process the image in parallel was also added, made possible in a similar fashion as shown in the second laboratory, specifically in the multiply_outer exercise. It also uses thread_func to create the pthreads.

The thread_func function is a thread function that processes a portion of the image; it calculates the start and end integers, that are used for the rescaling of a portion of the image and storing the result in the new_image field of the thread-specific data structure.

