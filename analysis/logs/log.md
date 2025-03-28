# Weekly/Bi-Weekly Log

## Prompts
Following the [Rose/Bud/Thorn](https://www.panoramaed.com/blog/rose-bud-thorn-activity-and-worksheet#:~:text=%22Rose%2C%20Bud%2C%20Thorn%22%20is%20a%20mindful%20design%2D,day%2C%20week%2C%20or%20month.) model:

### Date: 
March 28, 2025


### Number of hours: 
~45 hours (including missed earlier Weeks )

- Initial setup, debugging (local, Colab, Engineering SSL VPN, HPC): 15 hrs
- Florence-2 integration & HuggingFace cache management: 10 hrs
- Preprocessing pipeline setup (Whisper, frame extraction, alignment): 10 hrs
- Literature review and documentation writing: 6 hrs
- Model testing, training loop implementation, and GPU optimization: 4 hrs

Note: This log includes progress from previous missed submissions. The following summary captures the key highlights, learnings, and challenges from the beginning of the project.

### Rose:
The most rewarding progress was successfully fine-tuning Florence-2 using multimodal data (video frames + dialogues) on the MELD dataset. After an extensive debugging process, I was able to run the model on our Engineering SSL VPN-based multi-GPU server (2 GPUs). I also completed a clean Florence2-compatible training loop and incorporated proper memory handling and multiprocessing support. Seeing the first full epoch complete with consistent validation loss was a big milestone!

### Bud: 
I'm looking forward to refining the emotion mapping logic, evaluating Florence-2 predictions at a per-class level, and experimenting with lightweight data augmentation for text and vision inputs. There's also scope to eventually integrate reinforcement learning principles by shaping a reward function from Florence-2's embeddings or confidence scores. I'm also excited to optimize preprocessing GPU usage further, particularly for Whisper and CLIP (if reintroduced).

### Thorn: 
- Handling Florence-2 model compatibility in remote HPC environments was tricky due to missing transformers_modules cache and large model size (~3GB+), which couldn't be directly uploaded.
- Faced HuggingFace AutoModel errors when Florence2 was not registered correctly—solved by copying local cache and revising model loading with trust_remote_code=True.
- Whisper fallback warnings due to missing Triton/CUDA kernels required extra environment tweaks.
- Model saving in DataParallel mode caused attribute errors (save_pretrained()), which I fixed with proper model.module.save_pretrained() calls.

## Additional thought
None.

---

