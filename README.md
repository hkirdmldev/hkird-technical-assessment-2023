# HKIRD Technical Assessment

Hello and congratulations on making it to this stage of the interview process with the HKIRD team! We believe in a hands-on approach to assess the skills and knowledge of our potential candidates. This assessment will provide an opportunity for you to showcase your expertise.

Below are the instructions for the tasks you need to complete. Please read them carefully and ensure all requirements are met.

## Part 1: Data Handling and Model Training

### Requirements:

1. **Data Extraction**:
    - Begin by unzipping the `data.zip` folder.
    - Within the unzipped `data` folder, you'll find a `train` subfolder containing the training set images.

2. **Image Naming and Labeling**:
    - The class label of each image can be deduced from its parent folder. For instance:
      - Image at path `train/0/43.jpg` corresponds to class label 0.
      - Image at path `train/5/94.jpg` corresponds to class label 5.

3. **Data Analysis, Cleaning, and Transformation**:
    - Perform an analysis of the dataset.
    - Carry out necessary data cleaning and transformations.
    - Ensure your transformations cater for the potentially varying image sizes.

4. **Model Training**:
    - Build and train a machine learning or deep learning model using the transformed dataset.
    - Ensure that you have implemented measures to ensure you are not overfitting and can perform decently with unseen data.

5. **Jupyter Notebook**:
    - All the above tasks should be performed in a Jupyter Notebook (.ipynb).
    - The notebook should be structured, with appropriate analysis and documentation, to showcase your skills and proficiency.
    - Once completed, save the notebook. Also, convert the notebook into a .html file using the command:
    ```bash
    jupyter nbconvert <your_notebook_name>.ipynb --to html
    ```
    OR
    - In your jupyter notebook, File --> Save and Export Notebook As --> HTML

## Part 2: Model Deployment

### Requirements:

1. **FastAPI Deployment**:
    - By the end of Part 1, you should have a trained model.
    - Your task is to serve this model using FastAPI.

2. **Docker Containerization**:
    - Containerize your FastAPI application using Docker.
    - The container should be set up such that it can execute the script provided below, which fetches predictions for images located in `./data/sample_test folder`.
    - Build your image and run using `docker run --rm -p 1234:80 hkird_submission`.
    - Please strictly follow the image name, host port and container port above.

3. **Testing Your API**:
    - Make sure you successfully run `docker run --rm -p 1234:80 hkird_submission`
    - Pay close attention to the url below.
    - Ensure the API correctly returns predictions when running the given script:
    ```python
    import requests

    image_file_path = "./data/sample_test/54.jpg"

    url = "http://127.0.0.1:1234/predict/"

    with open(image_file_path, "rb") as image_file:
        files = {"file": image_file}
        response = requests.post(url, files=files)

    prediction = response.json()['prediction']
    # example prediction
    print(prediction)
    > 3
    ```
    - Your API must be built in a way such that the above code can be executed without problem.


4. **Exporting Docker Image**:
    - Once everything is set up, export your Docker image as a hkird_submission.tar file.
    - You MUST use `docker save hkird_submission -o hkird_submission.tar` to prevent different OS save and loading problems.
    - Please do sufficient testing that loading your .tar file and running the image also works using `docker load -i hkird_submission.tar`
    - Please zip the .tar file before uploading it. This will help keep the size of the .tar file below 1GB which is important for submission.

## Submission Instructions:

Please ensure that all the below files are included in your submission:

1. Your Jupyter notebook (.ipynb)
2. The HTML version of your Jupyter notebook (.html)
3. The Docker saved image (hkird_submission.tar) or zipped
4. A details.json file with the following details (example below):
{
    "name":"Chan Tai Man",
    "email": "chantaiman@gmail.com
}

Package all the above files into a .zip file, and create a new repository on GitHub (sign up for an account if you don't have), and upload the .zip file in the repository. It is essential that you make sure your .tar file is not corrupted during uploading of the .zip file. Lastly, send an email to irdmanulife@gmail.com with the title subject "HKIRD Technical Assessment Repository-(YOUR NAME)". You must submit your work within 5 days of beginning the assessment

Best of luck with the assessment! We look forward to reviewing your submission.
