# dompdfbundle

# HOW TO USE
add this codes into your controller

	function __construct(){
		parent::__construct();
		require_once APPPATH.'third_party/dompdf/dompdf_config.inc.php';
  }

public function cetak(){
		$dompdf = new Dompdf();

		$data = array(
					"nama" => "Akbar Abustang",
					"title" => "Programmer"
		);
 
		$html = $this->load->view('welcome_message',$data,true);

		$dompdf->load_html($html);

		$dompdf->set_paper('A4', 'landscape');

		$dompdf->render();

		$pdf = $dompdf->output();

		Output the generated PDF to Browser
		$dompdf->stream('laporanku.pdf', array("Attachment" => false));
		
	}

