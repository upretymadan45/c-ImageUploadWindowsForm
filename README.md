# c-ImageUploadWindowsForm
private void PictureBox1_Click(object sender, EventArgs e)
        {
            var openFileDialog = new OpenFileDialog()
            {
                FileName = "Select Image File",
                Filter="Select (*.jpg, *.png) | *.jpg; *.png;",
                Title="Select jpg or png image"
            };

            if (openFileDialog.ShowDialog() == DialogResult.OK)
            {
                var fileName = openFileDialog.FileName;
                var extension = Path.GetExtension(fileName);
                var newFileName = Guid.NewGuid().ToString() + extension;

                var destinationPath = $"{Directory.GetCurrentDirectory()}\\images\\{newFileName}";

                File.Copy(fileName, destinationPath, true);

                pictureBox1.Image = Image.FromFile(fileName);

                MessageBox.Show("File uploaded successfully");
            }
        }
