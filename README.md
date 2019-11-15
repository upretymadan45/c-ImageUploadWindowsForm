# c-ImageUploadWindowsForm

private void PictureBox1_Click(object sender, EventArgs e)
        {
            try
            {
                OpenFileDialog openFileDialog1 = new OpenFileDialog();

                openFileDialog1.Filter = "Image files | *.jpg";
                if (openFileDialog1.ShowDialog() == DialogResult.OK)
                {
                    var sourceFilePath = openFileDialog1.FileName;
                   
                    pictureBox1.Image = Image.FromFile(openFileDialog1.FileName);

                    var extension = Path.GetExtension(sourceFilePath);

                    destinationFilePath = "F:\\SEM IV\\6. Computer Project\\My Phone Book\\images\\" + GetUserId() + extension;

                    File.Copy(sourceFilePath, destinationFilePath,true);
                    
                }
            }
            catch (Exception ex)
            {
                MessageBox.Show(ex.Message);
            }
        }
