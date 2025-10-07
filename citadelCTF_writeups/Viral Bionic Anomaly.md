# Description
This floor is haunted by a phantom of the past. You encounter a presentation created by the last employee of a forgotten corporation, made just minutes before the Citadel awoke.

Rumor has it that the corporation predicted the rise of the Citadel. Within the slides, a "starter pack" holds the clues you need. Use it to confront the "final boss," a threat trapped inside a macro hidden deep within the presentation, and claim the key to the next floor.

# Solve

Ran OfficeMalScanner to extract the Vba bin file checked through the code seen it decoding from b64, b16, b32 combined those together to get "code" saw the first few bits that represented a jpeg file "FF D8 FF E0"
so saved that data as a jpeg and the flag was in the jpeg.

`Flag: citadel{gr4b_y0ur_l4bubus_m4tch4s_4nd_dub41_ch0c0l4t3s_y0u_4r3_1n_f0r_4_r1d3}`
