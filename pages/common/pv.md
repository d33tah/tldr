# pv

> monitor the progress of data through a pipe

- Print the contents of the file and display a progress bar:

`pv {{file}}`

- Measure the speed and amount of data flow between pipes (`-s` is optional):

`command1 | pv -s {{expected_amount_of_data_for_eta}} | command2`

- Recompress a file, also see the uncompressed and recompressed file size:

`pv -cN gz file.gz | gzcat | pv -cN uncompressed | xz | pv -cN xz > out.xz`

- Attach to an already running process and see its file reading progress:

`pv -d {{PID}}`

- Read an erroneous file, skip errors as `dd conv=sync,noerror` would:

`pv -EE {{path_to_faulty_media}} > image.img`

- Stop reading after reading specified amount of data, rate limit to 1K/s:

`pv -L 1K -S {{maximum_file_size_to_be_read}}`
