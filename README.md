# resume_as_code

Welcome to the **resume_as_code**! This project automates the process of generating a professional CV using a LaTeX template. The workflow is integrated with GitHub Actions, allowing you to automatically generate and update your CV whenever changes are made.

## Getting Started

Follow these steps to quickly start working on this project:

1. **Fork the Repository**:
   - Start by [forking this repository](https://github.com/AJLab-GH/resume_as_code/fork) to your own GitHub account.

2. **Clone the Repository**:

   - Clone the forked repository to your local machine:

     ```bash
     git clone https://github.com/YOUR_USERNAME/resume_as_code.git
     cd resume_as_code
     ```

3. **Set GitHub Action Permissions**:
   - In your `resume_as_code` repository settings, navigate to `Actions -> General` and ensure to set your `Workflow permissions` to **Read and write permissions** and choose to **Allow GitHub Actions to create and approve pull requests**.

   ![GitHub Actions Workflow Permissions](images/workflow-permissions.png)

4. **Customize Your CV**:
   - Open `resume.tex` and customize the template with your personal information. This file is where you define all the content for your CV.

5. **Customize the Output Resume Name**:
   - If you wish to change the default name of the generated resume, update the following lines in the GitHub Action file:
     - Open `.github/workflows/convert-and-upload.yml`.
     - Edit lines 25, 26, and 40 to replace `"Alexandre_Jammes_CV"` with your desired resume file name.

     Example:

     ```yaml
     - name: Export CV as PDF
       run: |
         pdflatex -output-directory=../outputs "resume.tex"
         mv ../outputs/resume.pdf ../outputs/Your_Name_CV.pdf```

     ```yaml
     - name: Move PDF to outputs directory
       run: |
         mkdir -p outputs
         mv YOUR_NAME_CV.pdf outputs/```

   - After making these changes, commit and push the updated workflow file:

     ```bash
     git add .
     git commit -m "<depict the changes you made>"
     git push origin main
     ```

6. **See Your New CV**:
   - Once your changes are pushed, GitHub Actions will automatically compile your LaTeX file and generate a PDF of your CV. You can find the generated CV in the `outputs` folder.

## How It Works

This repository uses a LaTeX template from [Overleaf](https://www.overleaf.com/latex/templates/john-miller-cv/djrtsjfvqmnq) that is to be customized to include your personal values. Once you've personalized `resume.tex` and pushed your changes to GitHub the remainder of process is fully automated through GitHub Actions:

- **LaTeX Template**: The `resume.tex` file contains the structure and content of your CV. Customize this file to suit your needs.

- **Automated Workflow**: Each time you commit changes to the `main` branch, GitHub Actions will:
  - Compile the LaTeX file into a PDF.
  - commit the generated PDF back to the repository in the `outputs` directory.

## Why This Approach?

This approach allows you to focus on the content of your CV while automating the generation process:

- **Focus on Content**: Update your CV content easily without worrying about the compilation process.
- **Consistency**: Ensure that your CV is always up-to-date and professionally formatted.
- **Automation**: GitHub Actions handle the compilation and version control, reducing the need for manual intervention.

## Contributing

Contributions are welcome! If you have suggestions for improving the workflow or the template, feel free to open a pull request.

## License

This project is open-source and available under the [MIT License](LICENSE).
