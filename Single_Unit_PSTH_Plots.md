### PSTH for all conditions and contrasts
This code utilizes single-unit electrode data. The output creates 20 (2 columns by 10 rows) Peri-Stimulus Time Histogram plots. These plots were based of of 10 different stimulus intensities where spacetimes of electrodes were measured.

I found this code to be one of the most difficult codes I had created in my short coding lifespan.


```
fig, axs = plt.subplots(len(contr_levels), len(conditions[::-1]), figsize=[15,15], sharex=True, sharey=True)

y_max = 0

for t, x in enumerate(contr_levels):
    for j, c in enumerate(conditions):
        for r in trials:
            spike_times = df[(df.neuron == 'm1_6') & (df.condition == c) & (df.contrast == x) & (df.repetition == r)]['spiketime']
            axs[t, j].hist(spike_times, bins=100)
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
    for d, n in enumerate(conditions):
        axs[a, d].set_ylim(0, y_max)
fig.suptitle('m1_6 neuron')
plt.tight_layout()
plt.show()
```

Output:

![Screenshot 2021-11-18 161752](https://user-images.githubusercontent.com/94637743/142490436-109a5cc0-05ce-4bdd-b642-6855b05bb544.jpg)
![Screenshot 2021-11-18 161829](https://user-images.githubusercontent.com/94637743/142490452-41f2493a-efbc-4c0b-8b85-430b02c415b8.jpg)




