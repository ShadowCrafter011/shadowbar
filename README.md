# Shadowbar, a simple process based progress bar

## Getting started
```python
from shadowbar import ProgressBar

progress, pbar = ProgressBar.new(length, total, refresh_rate=0.5)
```

### Parameters
- Length specifies the amount of characters the progress bar will span in the console
- Total specifies the amount of tasks that will be executed
- Refresh rate is the delay between updates. To short delays will lead to flickering in the console. The recommended and default value is 0.5

### Returns
- Progress is an integer shared value `from multiprocessing import Value`
- Pbar is the ProgressBar object instantiated through `ProgressBar.new()`

## Examples
```python
from shadowbar import ProgressBar
from time import sleep

progress, pbar = ProgressBar.new(50, 100)

for _ in range(100):
	progress.value += 1
	sleep(0.5)

pbar.wait_complete()
print("Task is done!")
```
`pbar.wait_complete()` ensures that the process is done before continuing
