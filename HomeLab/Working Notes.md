
aaea4b0f-fad7-4592-9fe6-b0beaa42ff7b


01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP104 [GeForce GTX 1070] [10de:1b81] (rev a1)
01:00.1 Audio device [0403]: NVIDIA Corporation GP104 High Definition Audio Controller [10de:10f0] (rev a1)


options vfio-pci ids=10de:1b81,10de:10f0 disable_vga=1


/goal i want to figure out what is the best local llm setup possible in the current vm using only the resources allocated to this vm. the setup would later need to be able to be accesed through an ai harness vm that i am going to setup later which will offload some tasks (smaller tasks or tasks that can take longer so maybe two different models depending on the situation if that is possible but test for both scenarios) to this local llm to handle. the harness will be using codex as the main brain. for now i need to figure what is the best possible setup to get the most performance out of the hardware/resources allocated to this vm in safe and stable way. as susch i need you to carry out testing in this vm (llm-gpu). create a folder where you will put all results of all your testing. i do not want gpu tempertaures  to go over 72C and should stay in the the 60s. make sure you are safe with the hardware. test the the gpu limits first.