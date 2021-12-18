### PSTH for all conditions and contrasts
This code utilizes single-unit electrode data. 
The output creates 20 (2 columns by 10 rows) Peri-Stimulus Time Histogram plots. 
These plots were based of of 10 different stimulus intensities 
where spacetimes of electrodes were measured. 
For loops are a powerful tool that allows me to utlize code 
to run the same code for multiple participants. 
For long loops like this it is best to go one line at a time and 
explain to yourself what you are trying to do with this line. 
Its easier to figure it all out for one participant first and then altering it to fit the rest of the participant data.  

I found this code to be one of the most difficult codes I had created in my short coding lifespan.


```
fig, axs = plt.subplots(len(contr_levels), len(conditions[::-1]), figsize=[15,15], sharex=True, sharey=True)

y_max = 0

for t, x in enumerate(contr_levels):
    for j, c in enumerate(conditions[::-1]):
#         for r in trials:  # removed this loop level and one indent for loop body
        spike_times = df[(df.neuron == 'm1_6') & (df.condition == c) & (df.contrast == x)]['spiketime']  # removed `& (df.repetition == r)`
        axs[t, j].hist(spike_times, bins=range(0, trial_length, 100), color='pink')
        axs[t, j].axvspan(stim_on_time, stim_off_time,
                  alpha= x / (max(contr_levels) * 2),
                  color='grey')
    axs[t, 0].set_ylabel(str(x) + "%")
    axs[t, 1].set_ylabel("Number of Spikes")
    if t == 0:
        axs[t, 0].set_title('Control Condition', fontsize=10)
        axs[t, 1].set_title('Adaptation Condition', fontsize=10)
    if t == 9:
        axs[t, 1].set_xlabel('Time (ms)')
        axs[t, 0].set_xlabel('Time (ms)')
    cur_min, cur_max = axs[t, j].get_ylim()
    if cur_max > y_max:
        y_max = cur_max
for a, v in enumerate(contr_levels):
    for d, n in enumerate(conditions[::-1]):
        axs[a, d].set_ylim(0, y_max)
fig.suptitle('m1_6 neuron')
plt.tight_layout()
plt.show()
```

Output:

![image](https://user-images.githubusercontent.com/94637743/146644733-4fab2f8e-9219-4353-bda4-b93fa2363060.png)


