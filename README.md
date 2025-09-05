COMMUNICATIONS SUBSYSTEMS

RESOURCES USED : 
GEMINI 2.5 PRO
CHAT-GPT


PHASE _1_ TIMING : 

Modules used: 
numpy
requests
io

APPROACH :
BPSK receiver is used.
Filtering: It first applies a matched filter to maximise the signal-to-noise ratio.
Decoding: It makes a hard decision on each cleaned-up symbol to convert it back into a '1' or '0'.
Calculates the Bit Error Rate (BER) by comparing its decoded bits to the original clean_bits.

FAILURES AND FIXES : 
Imperfect Timing. Errors are high. High BER value.

PROMPTS : 
1)I have a numpy file and a JSON file with the samples per symbol. Implement a receiver to recover bitstreams from the numpy file. Calculate the BER value and save the decoded bits in a separate file.
2)Decrease the ber value
3)How do i import the necessary modules in Jupyter Notebook?
Pickling error

DIFFERENCE BETWEEN THE EARLIER CODE AND THE IMPROVED VERSION : 
Filtering: Root-Raised Cosine (RRC) filter.
Phase Correction: Phase-Locked Loop (PLL).

PROMPT FOR THE IMPROVED VERSION : 
1) Modify the code in such a way that the BER value is reduced. Add appropriate filters. Make the changes and give me the complete code."
Pickling error

DIFFERENCE BETWEEN THE IMPROVED AND THE BEST VERSION : 
Timing recovery: Gardner Timing Recovery algorithm, Phase-Locked Loop (PLL)

PROMPTS : 
I have a numpy file and a JSON file with the samples per symbol. Implement a receiver to recover bitstreams from the numpy file. Calculate the BER value and save the decoded bits in a separate file.
Try to reduce the BER value further and save the decoded bits in a separate file.
Decrease the ber value
How do i import the necessary modules in Jupyter Notebook?
Pickling error

-----------------------------------------------------------

PHASE _2_ SNR : 

MODULES USED : 
numpy
json
requests
os
urllib
scipy
matplotlib

IMPAIRMENT PRODUCED: SNR scaling inconsistency

APPROACH : 

Matched Filtering (RRC Filter): Root-Raised Cosine filter (RRC)
Presenting QPSK BER performance and Constellation diagrams.

FAILURES AND FIXES :
Synchronisation is basic. 
Only works for QPSK.
Improvement: Use Costas Loop.

PROMPTS : 
I have a numpy file and a JSON file with the samples per symbol. Implement a receiver to recover bitstreams from the numpy file. Calculate the BER value and save the decoded bits in a separate file.
Try to reduce the BER value further and save the decoded bits in a separate file.
Decrease the ber value
How do i import the necessary modules in Jupyter Notebook?
Pickling error

-----------------------------------------------------------------

PHASE _3_ CODING : 

MOFULES USED : 
numpy
json
galois
commpy
Trellis
viterbi_decode

REED SOLOMON ERROR CORRECTION : 

APPROACH : (1)
USE RS(15,11) AND VITERBI DECODING
QPSK + Soft Demodulation:

FAILURES AND FIXES : 
The code assumes the data stream starts perfectly aligned.
Bit Packing
Fix: Use trellis termination.

PROMPTS :
I have a numpy file and a JSON file with the samples per symbol. Implement a receiver to recover bitstreams from the numpy file. Calculate the BER value and save the decoded bits in a separate file.
Try to reduce the BER value further and save the decoded bits in a separate file.
Decrease the ber value
How do i import the necessary modules in Jupyter Notebook?
Pickling error
---------------------------------------------------------------------

CONVOLUTION ERROR CORRECTION

MODULES USED : 
numpy
json
galois
commpy
Trellis
viterbi_decode


APPROACH :
Perform hard decision demodulation.
Perform soft decision demodulation by estimating noise and calculating Log-Likelihood Ratios (LLRs)
Calculate BER for Viterbi decoding with soft and hard decisions.

FIXES AND FAILURES :
Timing Error: Incorrect sampling
Use Costas loop
Ensure decoder parameters match the encoder.

PROMPTS : 
I have a numpy file and a JSON file with the samples per symbol. Implement a receiver to recover bitstreams from the numpy file. Calculate the BER value and save the decoded bits in a separate file.
Finally, add functions to calculate BER/FER, plot the constellation and LLR histogram, and compare the performance of hard demodulation and Viterbi decoding.
Pickling error

---------------------------------------------------------------

PHASE _4_ DOPPLER

Modules used : 
os
json
numpy
matplotlib.pyplot
scipy
fftconvolve

Required insight: Frequency offset estimation and correction

APPROACH :
Filter matching: Maximise SNR
Gardner Timing Recovery
Costas Loop
Soft-decision Log-Likelihood Ratios (LLRs)

FAILURES AND FIXES : 
High BER and FER values
Final constellation is rotated (90/180/270) degrees.

PROMPTS : 
I have a numpy file and a JSON file with the samples per symbol. Implement a receiver to recover bitstreams from the numpy file. Calculate the BER value and save the decoded bits in a separate file.
Plot the constellation diagrams.









