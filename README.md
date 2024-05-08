# 1.2 Understanding how it works
After adding another print line just after the spawn, this is what I received when triggering `cargo run` in the terminal:

![Img1](img\10-1.jpg)

As shown in the picture above, `Alma's Komputer: hey hey` was printed first before all others. This is because the line is placed **_after_** the spawner has spawned tasks into the queue but **_before_** those tasks are run by the executor (`executor.run();`).