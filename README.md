# 1.2 Understanding how it works
After adding another print line just after the spawn, this is what I received when triggering `cargo run` in the terminal:

![Img1](img\10-1.jpg)

As shown in the picture above, `Alma's Komputer: hey hey` was printed first before all others. This is because the line is placed **_after_** the spawner has spawned tasks into the queue but **_before_** those tasks are run by the executor (`executor.run();`).

<br>

# 1.3 Multiple Spawn and Removing Drop
When removing the `drop(spawner);` line, this is what my console looks like after running the program:

![Img2](img\10-2.jpg)

After adding the `drop(spawner);` back in and running the program again, this is what it looks like:

![Img3](img\10-3.jpg)

When I didn't drop the spawner, the program kept running & I had to force quit it on my console to make it stop. On the other hand, when I dropped the spawner again, the program immediately stopped once the last message was printed.

This is because when the spawner isn't dropped, the executor won't know it already finished spawning & will instead continue to listen for more tasks. In contrast, dropping the spawner notifies the executor that there won't be any more tasks being spawned, so it'll terminate as soon as all currently queued tasks are done.