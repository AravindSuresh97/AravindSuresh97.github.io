# Resolving Export Errors: Installing XeLaTeX and Pandoc for Jupyter Notebooks

Have you ever encountered frustrating errors while exporting Jupyter Notebooks? <br>
I recently found myself in a similar predicament when attempting to export my notebooks to PDF and other formats. <br>

![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/f7fa0078-f263-46c2-9430-e21aef484a49)


The culprit? Missing dependencies: **XeLaTeX and Pandoc**.

Now, you might be wondering, why were these dependencies missing in the first place? <br>
Well, it's not uncommon for certain software packages or tools to require additional components for specific functionalities. <br>
In the case of Jupyter Notebook exports, 
- XeLaTeX is often necessary for generating PDF files, while
- Pandoc facilitates conversions to various other formats.

In my case, these dependencies were not installed by default, leading to export errors. 
However, armed with this knowledge, I quickly set out to resolve the issue. 
First, I installed XeLaTeX, a typesetting system that provides extensive support for Unicode and complex scripts. 
You can do this by running the command:
```
sudo apt-get install texlive-xetex texlive-fonts-recommended texlive-plain-generic
```
Next, I installed Pandoc, a versatile document converter capable of transforming files between different formats.<br>
I did this my running the command:
```
sudo apt-get install pandoc
```

Once you've installed Pandoc and XeLaTeX (TeX) (if necessary), try exporting your Jupyter Notebook to PDF again.<br>


![image](https://github.com/AravindSuresh97/AravindSuresh97.github.io/assets/138949012/8b097c90-b27b-41a4-87ea-88a9378e8b6a)

<br>
If you get the above file dialogue, you have successfully exported it error-free!<br>
After installing Pandoc and XeLaTeX , I retried the export process, and this time, it went off without a hitch!

Happy Exporting 🤟 !!!
