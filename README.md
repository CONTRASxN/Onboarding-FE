# Frontend Task: "Questionnaire Runnable"

## Task Overview:

Your task is to create a dynamic and interactive questionnaire application using React. The application will be based on provided mock data and will have specific functionalities and components as outlined below.

### Requirements:

#### 1. Set Up:
- Initialize a new React project.
- Integrate the provided mock data, including:
  - Questionnaire meta information.
  - A sequence of objects consisting of Questions, Images, and potentially Videos.

#### 2. Components:
- **Questionnaire Wrapper Component**:
  - Display meta information initially.
  - Handle the rendering of different sequences based on their type.
    - Provided Types: Video and Question only. 
  - Implement logic for question navigation, allowing or restricting back-and-forth movement.
  - Options to either send data at the end of the questionnaire or after each question.
    - Add an Entrypoint for sending Data without actually sending data anywhere. 
    - Console.log or saving to file is fine.

- **Question Component**:
  - Based on the type of the question (Text, Integer, SingleChoice or Pairs), render the appropriate answer component.
  - Show the question
  
- **Answer Components**:
  - Create individual components for Text, Integer, Pairs and SC String answers.
  - Ensure accurate and user-friendly input validation.

- **Video Component** (if feasible):
  - Render a component that can play a video from a provided URL.
  - Any possibility to check if the Video has been fully played? 
  - Possible to limit fast / slow, going back or forth? Replay?

#### 3. Functionality:
- Load the mock data when the homepage is accessed.
- Save responses in real-time, maintaining the capability to send them back to the server upon request.
- Implement Features/Flags in the QuestionnaireWrapper for:
  - Enabling or disabling the redoing of questions.
  - Choosing between sending data after the completion of each question or only at the end of the questionnaire.

### Design and Responsiveness:
- The design should be functional, with an open choice of style (consider using Material UI for design components).
- Focus on responsiveness for desktops and laptops, don't over do it :).



### Some More informations
Each question gets answered by the following format. 
```
{
	"questionnaire": # Questionnaire ID,
	"question_id": # Question ID which is answered,
	"last_question_id": # ID of the last question answered,
	"content": {"text": # Question Text},
	"answer": # See AnswerType Specific Definition
}
```

Depending on the AnswerType of a Sequence in the Mock Data with "type":"question" a different Question Response Key "answer" Value Pair is expected.

**Type "text"**
```
"answer":{"value": Response Text}
```

**Type "single_choice_integer"**
```
"answer":{"key": # Corresponding Key as int, "value": # Selected Value}
```

**Type "integer"**
```
"answer":{"value": # Choosen Value}
```

**Type "pairs"**
Pairs is somehow special as it also contains a contentType for broader restriction. This Questionnaire only has "year" as contentType. 
```
"answer":{"values": # Dict: {# Mappings Key:Value}}
```


I hope the given answer_configs for each question provide enough informations about the answer boundaries, if not just ask or do how you interpret it yourself. 