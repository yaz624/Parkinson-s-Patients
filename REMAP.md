# Parkinson-s-Patients

![image](https://github.com/user-attachments/assets/a3d473ca-596b-4cae-99ec-cae76d855a9c)
Dataset name: REMAP Open dataset

Title: REMAP: a dataset of REal-world Mobility Activities in Parkinson's disease

Creator of this readme file: Catherine Morgan (ORCID ID 0000-0003-0333-2417), corresponding author Emma L. Tonkin (ORCID ID 0000-0001-7405-4982)

Data Steward: Ian Craddock (ORCID ID 0000-0001-6552-8541)

Data produced in: PD SENSORS study, University of Bristol study reference number 2018-4247

Study protocol: Morgan C, Craddock I, Tonkin EL, et al. Protocol for PD SENSORS: Parkinson’s Disease Symptom Evaluation in a Naturalistic Setting producing Outcome measuRes using SPHERE technology. An observational feasibility study of multi-modal multi-sensor technology to measure symptoms and activities of daily living in Parkinson’s disease 
                BMJ Open 2020;10:e041303. doi: 10.1136/bmjopen-2020-041303 

Overview of Open dataset contents:

1. 2D/3D skeleton video data containing turning of gait episodes

2. 2D skeleton video data containing sit-to-stand (STS) episodes

3. Human rater label dataset in excel spreadsheet format for 
	a) turning of gait: Turning_human_labels.xls
	b) sit-to-stand: SitToStand_human_labels.xls

4. Consent forms and Participant Information Sheets
	Contents of this folder "Consent forms_PIS":
		Consent form HV control.pdf = Blank consent form filled in by all the control participants.
		Consent form PwP.pdf = Blank consent form filled in by all the participants with Parkinson's disease.
		PIS HV control.pdf = Participant Information Sheet for control participants.
		PIS PwP.pdf = Participant Information Sheet for participants with Parkinson's disease.

NB Data descriptor document entitled "REMAP: a dataset of REal-world Mobility Activities in Parkinson's disease" includes background and project summary, methods, data records, technical validation, usage notes, code availability.

Folder structure for REMAP Open dataset:

Open_dataset_REMAP
	Turning
		Data
			turning_human_labels
			turning_2D3D_skeletons_coarsened
				Turning_coarsen_CSV
					PtIDnumber_PD/C_n_(excel ID)
						input_2D
						input_3D
		Code
			2D_data_generation
			3D_data_generation
	SitToStand
		Data
			STS_human_labels
			STS_2D_skeletons_coarsened
		Code
			use_case_STS_code
	Consent forms_PIS

Hardware: 
	Cameras = Microsoft Kinects. RGB (red-green-blue) data frames from the Kinect are stored and then aggregated into an MPEG-4-encoded video file according to their timestamp. There is some potential for uneven video timings and precise times between frames may vary due to the characeristics of the sensor platform.
	The resulting video from these platforms is 640x480 pixels in resolution and captured at 30 frames per second.
	
Tabular data description:

Nomenclature for all individual files/folders containing the final sensor data for an individual STS or turning episode: Pt[unique ID number]_[PD/C]_n_[turn/STS episode number]

Data description for Turning Data stored in .CSV files

Turning 2D data:
The skeletal 2D data (x,y) coordinates stored in the .csv file have the following format:
1. Number of Rows: Indicate the number of frames present in the clip 
(e.g. Pt204_C_n_350\input_2D\keypoints.csv has 91 rows i.e. 91 frames of the clip)
2. Number of Columns (A to AH, 34 columns) : Each column indicates the (x,y) coordinate joint position values of 17 skeletal joints data starting with x0,y0, x1,y1,x2,y2………………..x17,y17 (total 34 columns)  

Turning 3D data:
The skeletal 3D data (x,y,z) coordinates stored in the .csv file have the following format
Number of Rows: Indicate the number of frames present in the clip 
(e.g. Pt204_C_n_350\input_3D\keypoints.csv has 91 rows i.e. 91 frames of the clip)

Number of Columns (A to AY, 51 columns) : Each column indicates the (x,y,z) coordinate joint position values of 17 skeletal joints data starting with x0,y0,z0, x1,y1,z1,x2,y2,z2,………………..x17,y17 (total 51 columns)  

Data description for STS Data stored in .CSV files

STS 2D data:
1. Number of Rows: Indicates the number of frames present in the clip 
2. Column A: # frame number
3. Column B: time (s) which gives an offset of the row of data relative to the starting timestamp (0) of the (.csv) file. The STS transition starts at time (s) = 2.
4. Number of other Columns (C to AZ, 50 columns) : Each column indicates the (x,y) coordinate joint position values of 25 skeletal joints data starting with x0,y0, x1,y1,x2,y2………………..x25,y25 (total 50 columns)  

Data description for turning and STS human rater label .xlsx files

Turning spreadsheet name: Turning_human_labels.xls

The human rater labels for turning of gait episodes in the .xlsx file have the following format
Number of Rows: Indicates the number of turning of gait episodes included in this dataset minus the headings row (e.g. XXXX.xlsx has 1750 rows, so 1749 turning of gait episodes)
Column Headings:
COLUMN LETTER	HEADING					DESCRIPTION
A		Turn ID					Unique number assigned to turning episode which corresponds with the sensor data files/folder names which include "n_[turn episode number]" for each individual turn.
B		Participant ID number			ID assigned to an individual participant.
C		PD_or_C					Type of participant (PD = person with Parkinson's disease; C = healthy control participant).
D		number_of_turning_steps			Number of steps taken by participant during their turning clip, starting after the initial foot stance, in integers.
E		turning_angle				Angle over which turn was taken, to nearest 45 degrees (e.g. range of turns assigned to 90_degrees was 67.5 to 112.5 degrees; range of turns assigned to 135_degrees was 112.5 to 157.5 degrees etc).  
F		type_of_turn				Where possible to define, each turn assigned to a type of turn: "pivot_turn" or "step_turn". Pivot turn = a turn in which one or both feet swivel in place to achieve the turning movement. Step turn = a turn achieved by three steps or more without pivoting.
G		turning_duration			Duration of turn in seconds.milliseconds.
H		On_or_Off_medication			Medication status. If healthy control participant: always "Control". If participant with Parkinson's disease: either "On medication" or "Off medication" (as defined by the person being in the practically-defined "Off" medication state having withheld their long and short-acting dopaminergic medications).
I		DBS_state				Deep brain stimulation status. If healthy control participant: always "Control". If participant with Parkinson's disease: either "On DBS" (deep brain stimulator switched on or within 1 hour of it being switched off), "Off DBS" (1 hour or longer after deep brain stimulator switched off until it is switched back on again) or "-" (no deep brain stimulator in situ).
J		clinical_assessment			"yes" indicating the turning episode took place while the participant was undergoing clinical assessments with a researcher, or "no" indicating that the turn was captured from free-living behaviour.

STS spreadsheet name: SitToStand_human_labels.xls

The human rater labels for STS episodes in the .xlsx file have the following format
Number of Rows: Indicates the number of STS episodes included in this dataset minus the headings row (i.e. SitToStand_human_labels.xls has 404 rows, so 403 STS episodes in total)
Column Headings:
COLUMN LETTER	HEADING					DESCRIPTION
A		Transition ID				Unique number assigned to turning episode which corresponds with the sensor data files/folder names which include "n_[STS episode number]" for each individual STS transition episode.
B		Participant ID number			ID assigned to an individual participant.
C		PD_or_C					Type of participant (PD = person with Parkinson's disease; C = healthy control participant).
D		sts_whole_episode_duration		Duration in seconds of "whole episode duration" label which started when the participant made their first motion towards standing from a static sitting position and ended when the person was fully upright.
E		sts_final_attempt_duration		Duration in seconds of "final attempt duration" label in milliseconds, comprising their impression of the duration between the lowest point of the head (start) and when the person was fully upright/the maximum vertical position of the vertex of the head (end). 
F		On_or_Off_medication			Medication status. If healthy control participant: always "Control". If participant with Parkinson's disease: either "On medication" or "Off medication" (as defined by the person being in the practically-defined "Off" medication state having withheld their long and short-acting dopaminergic medications).
G		DBS_state				Deep brain stimulation status. If healthy control participant: always "Control". If participant with Parkinson's disease: either "On DBS" (deep brain stimulator switched on or within 1 hour of it being switched off), "Off DBS" (1 hour or longer after deep brain stimulator switched off until it is switched back on again) or "-" (no deep brain stimulator in situ).
H		clinical_assessment			"yes" indicating the turning episode took place while the participant was undergoing clinical assessments with a researcher, or "no" indicating that the turn was captured from free-living behaviour.
I		STS_additional_features			A note to describe extra features of the STS episode: "slow" (subjective rating), "Uses arms of chair" (which denotes using nearby flat surface to lever up from chair to standing), "Moves forward in chair" (prior to standing up), ">1 attempt" (person tries more than once to get up before being successful), "Carrying something" (in hands), "Moves forward in chair" (prior to standing up), "unable to arise without help".
J		MDS-UPDRS_score_3.9 _arising_from_chair	A score from 0-4 assigned to each STS episode, with scoring criteria from the MDS-UPDRS (Movement Disorders Society-sponsored revision of the Unified Parkinson's Disease Rating Scale) part 3.9. 0 = normal; 4 = unable to arise without help.

Extra information about "on" and "off" medication labels: Throughout the dataset, the sensor data, human rater labels, clinical rating scale scores etc have often been assigned to "on" medications (with medications alleviating symptoms) or "off" medications (with increase symptom severity) for the person with Parkinson's. 
	"off" medications = the person with Parkinson's disease was in a practically-defined "off" medications state, having withheld their long-acting dopaminergic medications for >24 hours and their short-acting dopaminergic medications for >12 hours.
	"on" medications = the rest of the data was taken to be in the "on" medications state, i.e. the person had not withheld their dopaminergic medications for the pre-specified time periods (see above).

Software: 
	No particular operating system is required to make use of the data. 
	Any graphing package may be used to inspect the dataset. Any machine learning package, such as scikit-learn, may be used to make use of the data. 
	We provide sample code in Github for the sit-to-stand use-case of the dataset. 
