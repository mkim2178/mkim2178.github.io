Transfer learning is a technique where a pre-trained model, originally trained on a large dataset, is reused for a different but related task.
If we have a small dataset, we can use the pre-trained model and freeze the earlier layers to avoid overfitting, since those layers capture general patterns like edges, sounds, or basic shapes.
On the other hand, if we have a large dataset, we can unfreeze additional layers and fine-tune the entire model to improve performance.
This type of technique is efficient for save training time and boosting accuracy, especially when the amount of data is limited.
However, the key caution when using transfer learning is that the original task and the new task should be closely related. Otherwise, the model may perform poorly — a phenomenon known as negative transfer.


---
This summary is based on Andrew Ng’s *Machine Learning Specialization* [https://www.coursera.org/specializations/machine-learning-introduction] on Coursera.
